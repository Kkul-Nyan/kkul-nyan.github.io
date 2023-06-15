---
layout: page
title: TopDownKing
permalink: /TopDownKing/
image: TopdownKing.png
---

# TopDownKing

개발 환경: Mac Ventura<br>
개발툴: Unity 2021.3.24f1<br>
게임 이름: TopDownKing<br>
게임 장르: Topdown view FPS<br>
기획 의도: 빠르고 간편하게 즐기는 모바일 배틀로얄 게임<br>
다운로드 URL: https://drive.google.com/drive/folders/1g67VpUrbOjOg2KYSo8XiclkaqKwPVBBg?usp=sharing<br>
작업 기간: 2023.5.1 ~ 23.5.19<br>
프로젝트 완료일: 2023년 5월 19일<br>
플랫폼: Android, Ios,PC<br>


![Login]({{ site.baseurl }}/images/TopDownKing/login.gif)


![Main]({{ site.baseurl }}/images/TopDownKing/main.gif)


![Game]({{ site.baseurl }}/images/TopDownKing/game.gif)


## 프로젝트 기획


![01]({{ site.baseurl }}/images/TopDownKing/01.png)


## 사용 에셋

- TextMeshPro Version 3.0.6 - April 22, 2021
- Universal RP Version 12.1.8 - December 12, 2022
- Editor Console Pro Version 3.972 - April 08, 2023
- Rainbow Folders 2 Version 2.4.0 - May 07, 2022
- Battle Royale Hero PBR Version 1.1 - October 12, 2021
- Fun Casual Sounds Version 1.0 - June 01, 2016
- GUI PRO Kit - Casual Game Version 2.0.8 - April 14, 2023
- Input System Version 1.4.4 - November 03, 2022
- Custom Hierarchy for Unity Version 1.2.0
- ParrelSync Version 1.5.2
- PUN 2 - FREE Version 2.41 - August 02, 2022
- Odin Inspector and Serializer Version 3.1.12.2 - April 19, 2023

## **기능 구현 파트**

### GameManager

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class GameManager : MonoBehaviour
{
    public int mapSizeX;
    public int mapSizeZ;
    public int mapTileScale;
    public int charactorSelectNumber = 0;
	//유저가 가지고있는 코인의 갯수입니다. 플레이팹과 연동됩니다.
    public int userCoin;
	//유저가 지정한 사운드 크기입니다. 다른씬에서도 동일한 사운드크기를 제공하기위해 자기고있습니다.
    public float soundSize;
    
    public string userName;
    public bool isMute = false;

    //게임매니저는 유저정보등을 가지고 있기 떄문에 만들어준 싱글톤입니다. 
    public static GameManager instance;
    private void Awake() {
        if(instance == null){
            instance = this;
            DontDestroyOnLoad(instance);
            return;
        }
        Destroy(this.gameObject);
    }
    private void Update() {
        
    }

    // 사운드 크기를 조정합니다.
    public void SoundChange(){
        AudioListener.volume = soundSize;
    }

    //사운드 플레이를 중지합니다.
    public void MuteSound(){
        AudioListener.pause = isMute;
    }
}
```

### IteamData

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

//아이탬 종류를 간편하게 선택할수있게합니다.
public enum ItemType{
    Bullet,
    Consumable
}

//Consumable아이탬일 경우 어떤 Status와 연관되었는지 간단하게 관리하게해줍니다.
public enum ConsumableType{
    Health,
    Mana
}

// 아이탬을 한번에 관리하게 편하게 자료를모아주는 데이터타입입니다.
[CreateAssetMenu(fileName = "Item", menuName = "NewData")]
public class ItemData : ScriptableObject
{
    public string displayName;
    public string description;
    public ItemType type;
    //포톤인스턴스로 생성될 프리팹입니다.
    [PreviewField(100)]public GameObject dropPrefab;

    public ConsumableItemData consumable;
}

//Consumable아이탬일경우 어떤타입에 대응하고 얼마의 값을 변동시킬지 간단히 관리하게합니다.
[System.Serializable]
public class ConsumableItemData
{
    public ConsumableType type;
    public float value;
}
```

### PhotonCamera

```csharp
using UnityEngine;
using Photon.Pun;

public class PhotonCamera : MonoBehaviourPunCallbacks
{
    [SerializeField] private Transform target;
    [SerializeField] private Vector3 offset;
    [SerializeField] PhotonView pv;

    private void Start() {
		//카메라가 쫒아갈 캐릭터를 찾아줍니다.
        pv = GameObject.FindWithTag("Player").GetComponent<PhotonView>();
        if(pv.IsMine){
            target = GameObject.FindWithTag("Player").GetComponent<Transform>();
        }
    }

    private void LateUpdate()
    {
		//타켓을 기준으로 탑다운 방식으로 카메라를 컨트롤하게 됩니다.
		//오프셋을 통해 얼마나 타켓기준 떨어지거나, 어떤각도로 볼지를 컨트롤합니다.using System.Collections;
        transform.position = target.position + offset;
        transform.eulerAngles = new Vector3(60, 0, 0); 
    }
}
```

### Bullets

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Photon.Pun;
using Photon.Realtime;

public class Bullets : MonoBehaviourPunCallbacks
{
	//다른스크립트에서 인스턴스생성시 구분하기 위해 사용되는 id값입니다.
    public int bulletID;
    public PhotonView pv;
    public float speed;
    public int Damage = 50;
    public int manaDecoy;
    Rigidbody rig;
    public float limitTime = 3;
    private void Start() {
        rig = GetComponent<Rigidbody>();
        rig.AddForce(transform.forward * speed, ForceMode.Impulse);
        Invoke("selfDestroy", limitTime);
    }

	//생성된 이후 일정 시간뒤 자동 오브젝트 파괴합니다.
    void selfDestory(){
        pv.RPC("DestroyRPC", RpcTarget.AllBuffered);  
    }

	// 오브젝트를 맞췄을 때, Idamagable을 가지고있다면 데미지를 입히고 오브젝트를 파괴합니다
    private void OnCollisionEnter(Collision other) {
        var ob = other.transform.gameObject.GetComponent<IDamagable>();
        if(  ob != null)
            ob.TakePhysicalDamage(Damage);

        pv.RPC("DestroyRPC", RpcTarget.AllBuffered);
    }

	//오브젝트를 파괴합니다. 포톤RPC를 통해 모든 플레이어에게 전달합니다.
    [PunRPC]
    void DestroyRPC() => Destroy(transform.gameObject);
}
```

### ItemBullets

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class ItemBullets : MonoBehaviour
{
	// 아이탬데이터에 불렛의 인스턴스 및 대부분 정보를 가지고있습니다.
    public ItemData bulletData; 
	
    //플레이어가 총알아이탬에 닿는다면, 닿은 총알로 플레이어가 발사하는 총알을 변경한뒤 파괴됩니다.
    private void OnTriggerEnter(Collider other) {
        if(!other.gameObject.CompareTag("Player")){
            return;
        }
        if(other.gameObject.CompareTag("Player")){
            PlayerController player = other.gameObject.GetComponent<PlayerController>();
            player.bullet = bulletData.dropPrefab.GetComponent<Bullets>();
            
            Destroy(transform.gameObject);
        }
    }
}
```

### Potion

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Photon.Pun;
using Photon.Realtime;

//어떤종류의 Status에 작동하는지 구분하기 위한 enum입니다.
public enum PotionType{
    HPPotion,
    ManaPotion
}
public class Potion : MonoBehaviour
{
    private PhotonView pv;
    public int potionID;
    public float recoyValue;
    public PotionType type;
    PlayerStatus playerStatus;

    private void Awake() {
        pv = GetComponent<PhotonView>();
    }

	//플레이어가 포션을 닿게된다면, 플레이어의 Status를 가져오고 포션의 타입에 맞게 미리 설정된 Status를 증가시키고
	//포션프리팹을 파괴합니다.
    private void OnTriggerEnter(Collider other) {
        playerStatus = other.GetComponent<PlayerStatus>();
        if(playerStatus != null){
            switch(type){
                case PotionType.HPPotion :
                    playerStatus.health.Add(recoyValue);
                    pv.RPC("DestroyPotion", RpcTarget.AllBuffered);
                break;
                case PotionType.ManaPotion :
                    playerStatus.mana.Add(recoyValue);
                    pv.RPC("DestroyPotion", RpcTarget.AllBuffered);
                break;
            }
        }
    }
    
    //포톤RPC를 통해 오브젝트를 파괴합니다.
    [PunRPC]
    void DestroyPotion(){
        Destroy(transform.gameObject);
    }
}
```

### MapGenerator

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Photon.Pun;
using Photon.Realtime;

public class MapGenerator : MonoBehaviourPunCallbacks
{
    public int objectScale;
    public int mapSizeX = 10;
    public int mapSizeZ = 10;
    public int positionY;
    public int maxObjects;
    public int minObjects;
    
    public PhotonView pv;
    
    void Start()
    {
		//플레이어가 랜덤으로 생성될 범위를 지정해줍니다.
		GameManager.instance.mapTileScale = objectScale;
        GameManager.instance.mapSizeX = mapSizeX * objectScale;
        GameManager.instance.mapSizeZ = mapSizeZ * objectScale;
		//호스트가 방을만들어 접속할떄 실행되게합니다. 호스트외에 다시금 맵을 생성할 필요가 없으니 호스트만 작동시킵니다.
        if(PhotonNetwork.IsMasterClient){
            GenerateMap();
            GenerateEdge();
            ObjectGenerator();
        }
        CreatePlayer();
    }

    //맵타일을 제작하는 부분입니다.
    void GenerateMap()
    {
		//블록사이즈를 조정하면 서로 겹치는 문제가 생기기때문에, 스케일에 따른 위치값을 조정하게됩니다.
        GameManager.instance.mapTileScale = objectScale;
        GameManager.instance.mapSizeX = mapSizeX * objectScale;
        GameManager.instance.mapSizeZ = mapSizeZ * objectScale;

		// 간단한 패턴디자인을 통해 미리 지정된 x,z 사이즈 만큼의 맵을 만듭니다.
        for (int x = 0; x < mapSizeX; x++)
        {
            for (int z = 0; z < mapSizeZ; z++)
            {
                Vector3 tilePosition = new Vector3(x * objectScale, positionY, z * objectScale);
				//Resources폴더에있는 미리 지정된 블록을 생성합니다.
                PhotonNetwork.Instantiate("Maptile", tilePosition, Quaternion.identity);
            }
        }
    }

    //맵타일 주변 테두리 오브젝트를 만들어줍니다.
    void GenerateEdge(){
        for(int x = 0; x < mapSizeX; x++){
            Vector3 edgePosition = new Vector3(x * objectScale, Mathf.Abs(positionY * objectScale) - 1f, (mapSizeZ - 1) * objectScale);
            //Resources폴더에있는 미리 지정된 블록을 생성합니다
			PhotonNetwork.Instantiate("Maptile", edgePosition, Quaternion.identity);

            edgePosition = new Vector3(x * objectScale, Mathf.Abs(positionY * objectScale)-1, 0);
            PhotonNetwork.Instantiate("Maptile", edgePosition, Quaternion.identity);
        }
        
        for(int z = 1; z < mapSizeZ-1; z ++){
            Vector3 edgePosition = new Vector3((mapSizeX - 1) * objectScale, Mathf.Abs(positionY * objectScale) - 1f, z * objectScale);
            //Resources폴더에있는 미리 지정된 블록을 생성합니다
            PhotonNetwork.Instantiate("Maptile", edgePosition, Quaternion.identity);

            edgePosition = new Vector3(0, Mathf.Abs(positionY * objectScale) - 1f, z * objectScale);
			//Resources폴더에있는 미리 지정된 블록을 생성합니다
            PhotonNetwork.Instantiate("Maptile", edgePosition, Quaternion.identity);
        }
    }

    //맵내부 오브젝트를 제작하는 부분입니다.
    void ObjectGenerator(){
		// 미리 지정해둔 최대 생성갯수와 최소생성 갯수 사이의 랜덤한 값을 생성할 숫자로 가져옵니다.
        int totalObject = Random.Range(minObjects, maxObjects + 1);
        Vector3[] bannedPosition = new Vector3[totalObject];

        for(int i = 0; i < totalObject; i++){
            
		    //어떤 오브젝트를 만들지 랜덤으로 선택합니다.
            int selectRandomObject = Random.Range(0, 6);
			//오브젝트가 생성될 랜덤한 위치값을 생성합니다.
            int randomPositinX = Random.Range(objectScale, (mapSizeX - 2) * objectScale); 
            int randomPositinZ = Random.Range(objectScale, (mapSizeZ - 2) * objectScale);

            randomPosition = new Vector3(randomPositinX, Mathf.Abs(positionY * objectScale) - 1f, randomPositinZ);
			// 생성된 랜덤한 위치값이 기존에 오브젝트가 생성된 위치라면 재귀함수를 통해 다시 실행하게합니다.
            foreach(Vector3 pos in bannedPosition){
                if(pos == randomPosition){
                    ObjectGenerator();
                    return;
                }
            }
            // 미리 생성한 랜덤한 숫자에 맞춰서 Resources폴더에 만들어둔 오브젝트를 생성합니다.
            if(selectRandomObject == 0){
                PhotonNetwork.Instantiate("Stone1", randomPosition, Quaternion.identity);
            }
            else if(selectRandomObject == 1){
                PhotonNetwork.Instantiate("Stone", randomPosition, Quaternion.identity);
            }
            else if(selectRandomObject > 2){
                PhotonNetwork.Instantiate("Tree", randomPosition, Quaternion.identity);
            }
			//랜덤한값을 이제 중복생성이 되지않도록 저장해줍니다.
            bannedPosition[i] = randomPosition;
        }
    }
    void CreatePlayer(){
        PhotonNetwork.Instantiate("Player", transform.position, Quaternion.identity);
    }
```

### DestoryFloor

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Photon.Pun;
using Photon.Realtime;

public class DestoryFloor : MonoBehaviour
{
    Renderer renderer;
    public bool isPlayer = false;
    public float maxTime;
    float itime;
    public float destoryTime;
    bool isDestory = false;

    Color startColor;
    public Color destoryColor;

    public PhotonView pv;

    private void Start() {
		//필요값을 초기화합니다.
        renderer = GetComponent<Renderer>();
        startColor = renderer.material.color;
    }
    private void Update() {
        RemoveFloor();
    }
		
	//플레이어가 닿을경우, 색상을 변경합니다.
    private void OnCollisionStay(Collision other) {
        if(other.transform.CompareTag("Player")){
            ColorChangeFloor();
        }
    }
	//색상이 변경되는 경우 RPC를 통해 모든플레이어에게 동기화시킵니다.
    [PunRPC]
    void ColorChangeFloor(){
        //타임값에 따라 색상을 변경합니다.
        if (itime < maxTime)
        {
            itime += (float)(Time.deltaTime);
            float t = itime / maxTime;
            renderer.material.color = Color.Lerp(startColor, destoryColor, t);
        }
        else
        {
            renderer.material.color = destoryColor;
			//바닥오브젝트가 파괴되기전 바닥은 중력으로 인해 밑으로 떨어지게됩니다.
            transform.gameObject.AddComponent<Rigidbody>();
            isDestory = true;
        }
        
    }
	//바닥이 일정시간이 지나면 바닥을 파괴합니다. 모든플레이어에게 동기화 해줍니다.
    [PunRPC]
    void RemoveFloor(){
        if(isDestory == true){
            if(destoryTime > 0){
                destoryTime -= Time.deltaTime;
            } 
            else{
                pv.RPC("Die", RpcTarget.AllBuffered);       
            }
        } 
    }
	//파닥을 파괴하고, 모든플레이어에게 동기화해줍니다.
    [PunRPC]
    void Die() => Destroy(transform.gameObject);
}
```

### DropItem

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Photon.Pun;
using Photon.Realtime;

//어떤종류를 아이탬을 드랍하는지 간편하게 관리하기위해 만들었습니다.
public enum DropType {
    dropBullet,
    dropConsumableItem
}
public class DropItem : MonoBehaviourPunCallbacks
{
    public DropType dropType;
    public ItemData[] items;

//Drop이 실행되게되면, 미리 enum을 기반으로 선택한 dropType에 맞게 다음 스크립트를 작동합니다. 
    public void Drop(){
        switch (dropType) {
            case DropType.dropBullet :
                DropBullet();
            break;
            case DropType.dropConsumableItem :
                DropConsumableItem();
            break;
        }
    }
// dropType이 총알인 경우 작동하며, 총알인스턴스를 만들어줍니다.
    void DropBullet(){
        int dropItemNum = Random.Range(0, items.Length);
		// 혹시 총알타입의 아이탬이 아닐경우 작동을 멈춥니다.
        if(items[dropItemNum].type != ItemType.Bullet){
            DropBullet();
            return;
        }
        Bullets bullet = items[dropItemNum].dropPrefab.GetComponent<Bullets>();
		//transform.position으로 생성시 바닥오브젝트에 박히게 되어 보정값을 넣어주었습니다.
        Vector3 bulletPosition =  transform.position + new Vector3(0, 1, 0);
        PhotonNetwork.Instantiate("itemBullet" + bullet.bulletID, bulletPosition, Quaternion.identity);
    }

    // dropType이 소모아이탬인 경우 작동하며, 소모성아이탬을 랜덤하게 생성합니다.
    void DropConsumableItem(){
        int dropItemNum = Random.Range(0, items.Length);
        if(items[dropItemNum].type != ItemType.Consumable){
            DropConsumableItem();
            return;
        }
        Potion potion = items[dropItemNum].dropPrefab.GetComponent<Potion>();
        Vector3 rotation =  new Vector3(-90,0,0);
        PhotonNetwork.Instantiate("Potion" + potion.potionID, transform.position, Quaternion.Euler(rotation));
    }
}
```

### MapObject

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Photon.Pun;
using Photon.Realtime;

//인터페이스 IDamagable을 가져옵니다.
public class mapObject : MonoBehaviourPunCallbacks, IDamagable
{
    public PhotonView pv;
    public int maxHealth;
    public int curhealth;
    Renderer renderer;
    Color startColor;
    public Color destroyColor;
		DropItem dropItem;

 
    private void Start() {
        renderer = GetComponent<Renderer>();
        startColor = renderer.material.color; 
				dropItem = GetComponent<DropItem>();
    }

	// 인터페이스를 통해 필수적으로 작성해야합니다. 총알등이 적중했을때 데미지를 입히는데 사용합니다.
    public void TakePhysicalDamage(int amount){
        curhealth -= amount;
		//스크립트가 호출되면, RPC를 통해 색상 변경이 모든플레이어게 동기화하도록합니다.
        pv.RPC("HitColor", RpcTarget.All);
		//일정이하 체력이 되었을 때 오브젝트를 파괴하는 스크립트입니다.
        CheckDestroy();
    }
	
    //맵을 구성하는오브젝트를 파괴하는 스크립트입니다. 모든플레이어가 알아야하는 정보임으로 동기화합니다.
    [PunRPC]
    void Die() => Destroy(transform.gameObject);

	//RPC를통해 맵오브젝트 생상이 변경되면 모든플레이어에게 동기화 해줍니다.
    [PunRPC]
    void HitColor(){
        float  t = (float)(maxHealth - curhealth) / (float)maxHealth;
        renderer.material.color = Color.Lerp(startColor, destroyColor, t);
    }
	
    // 일정이하 체력이 되면 오브젝트를 파괴합니다.
    void CheckDestroy(){
        if( curhealth <= 0){
            pv.RPC("Die", RpcTarget.All);
			//파괴될시 아이탬을 생성합니다.
			dropItem.Drop();
        }
    }
}
```

### AutoOwnershipTransfer

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Photon.Pun;
using Photon.Realtime;

public class AutoOwnershipTransfer : MonoBehaviourPunCallbacks
{
    [SerializeField] private GameObject playerObject;
    private PhotonView photonView;

    
    void Start()
    {
        playerObject = GetComponent<GameObject>();
        photonView = playerObject.GetComponent<PhotonView>();
        if (photonView.Owner == PhotonNetwork.LocalPlayer)
        {
            photonView.TransferOwnership(PhotonNetwork.MasterClient);
        }
    }
	
    //호스트가 접속을 끊어졌을떄, 자동으로 미리지정된 오브젝트들을 새로운 호스트에게 오브젝트소유권을 이동시킵니다.
    public override void OnMasterClientSwitched(Player newMasterClient)
    {
        if (photonView.Owner == PhotonNetwork.LocalPlayer)
        {
            photonView.TransferOwnership(newMasterClient);
        }
    }
}
```

### NetworkManager

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Photon.Pun;
using Photon.Realtime;
using UnityEngine.UI;
using UnityEngine.SceneManagement;

//포톤과 연관된 스크립트입니다.
public class NetworkManager : MonoBehaviourPunCallbacks
{
    private void Awake() {
        //포톤서버와 얼마나 자주 데이터 송수신을 할지를 결정합니다.
        PhotonNetwork.SendRate = 60;
        PhotonNetwork.SerializationRate = 30;
    }
		
	// 포톤에서 랜덤한 방 참여를 시도합니다.
    public void JoinRandomRoom()
    {
		//닉네임을 저장해둡니다.
		PhotonNetwork.NickName = GameManager.instance.userName;
        PhotonNetwork.JoinRandomRoom();
    }

	// 랜덤한 방참여에 실패하면 랜덤한 방을 생성합니다.
    public override void OnJoinRandomFailed(short returnCode, string message)
    {
        Debug.Log("Join random failed, creating new room.");
        RoomOptions options = new RoomOptions {MaxPlayers = (byte) 4};
        PhotonNetwork.CreateRoom(null, options, null);
    }

    //방 접속시 게임1번 씬으로 이동합니다.
    public override void OnJoinedRoom()
    {
        //룸접속완료
        Debug.Log("현재 방 이름 : " + PhotonNetwork.CurrentRoom.Name);
        Debug.Log("현재 방 인원수 : " + PhotonNetwork.CurrentRoom.PlayerCount);
        Debug.Log("현재 방 최대인원수 : " + PhotonNetwork.CurrentRoom.MaxPlayers);
        Debug.Log("현재 방 열려있는지 : " + PhotonNetwork.CurrentRoom.IsOpen);
        Debug.Log("현재 방 비공개 여부 : " + PhotonNetwork.CurrentRoom.IsVisible);
        PhotonNetwork.LoadLevel(2);
    }

    // 방접속 종료시 메인화면씬으로 전환합니다.
    public override void OnDisconnected(DisconnectCause cause){
        SceneManager.LoadScene(0);
    }

    // 접속종료 버튼을 눌릴시 메인씬으로 돌아가고, 포톤서버에 재접속합니다.
    public void Disconnected(){
    PhotonNetwork.Disconnect();
    Connect();
    }
}
```

### PlayfabManager

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;
using PlayFab;
using PlayFab.ClientModels;
using TMPro;
using Photon.Pun;
using UnityEngine.UI;
using Photon.Realtime;

public class PlayFabManager : MonoBehaviourPunCallbacks
{
    public TMP_InputField loginEmailInput;
    public TMP_InputField loginPasswoadInput;

    public TMP_InputField registerUserNameInput;
    public TMP_InputField registerEmailInput;
    public TMP_InputField registerPasswordInput;

    public TextMeshProUGUI coinText;
    public CanvasGroup failCanvas;
    public Canvas successCoinCanvas;

    public AudioSource mainAudioSource;
    public AudioSource lobbyAudioSource;
    public AudioClip getCoinSound;

    public Button joinButton;

    public LoginMenuController loginMenuController;
    public AudioClip clickSound;

    float timer;
    float fadetime = 3f;
    bool isfade = false;

    private void Update() {
	    // 로그인이 실패시 로그인을 다시 시도하라는 캔버스를 서서히 사라지게합니다.
        if( isfade == true){
            FadeOutCanvas();
        }
    }

    //아이디, 비밀번호를 inputfield에 넣고 로그인 버튼 클릭시, Playfab에 로그인 요청을 합니다.
    public void OnLoginButton()
    {
		//버튼클릭시 클릭버튼을 재생합니다.
        lobbyAudioSource.Play();
		//중복된 접속시도를 막기위해 버튼클릭을 막아둡니다.
        joinButton.interactable = false;
        var request = new LoginWithEmailAddressRequest {Email = loginEmailInput.text, Password = loginPasswoadInput.text};
        PlayFabClientAPI.LoginWithEmailAddress(request, OnLoginSuccess, OnLoginFailure);
    }

    //아이디, 비밀번호, 유저네임(닉네임)을 작성하고 회원가입버튼을 클릭시, Playfab에 Rigister요청을 합니다.
    public void RegisterButton(){
        lobbyAudioSource.Play();
        var request = new RegisterPlayFabUserRequest {Email = registerEmailInput.text, Password = registerPasswordInput.text,Username = registerUserNameInput.text, DisplayName = registerUserNameInput.text};
        PlayFabClientAPI.RegisterPlayFabUser(request, OnRegisterSuccess, OnRegisterFailure);
    }

    // 로그인요청이 승인된다면 작동합니다. 
    private void OnLoginSuccess(LoginResult result)
    {
        // 플레이팹에서 플레이어 프로필 정보를 가져옵니다. 여기서는 닉네임에 사용할 username을 가져옵니다.
        PlayFabClientAPI.GetPlayerProfile( new GetPlayerProfileRequest() {
            PlayFabId = result.PlayFabId, 
                ProfileConstraints = new PlayerProfileViewConstraints() {
                    ShowDisplayName = true
            }
        },

        //정보를 가져오는데 성공했다면, 싱글톤인 게임매니저에 정보를 전달합니다.
        result => {
            GameManager.instance.userName = result.PlayerProfile.DisplayName.ToString();
            },
        error => Debug.LogError(error.GenerateErrorReport()));
				// 플레이팹에서 플레이어 경제에서 통화값을 가져옵니다.
        PlayFabClientAPI.GetUserInventory(new GetUserInventoryRequest(), (result) => GameManager.instance.userCoin = result.VirtualCurrency["CO"], (error) => Debug.Log("Failed Check Coin"));
        //플레이팹 기본적인 정보를 받은 다음, 포톤 서버접속 시도
        PhotonNetwork.ConnectUsingSettings();
        joinButton.interactable = true;
    }
    
    //포톤서버 접속 성공시 메인씬이동합니다.
    public override void OnConnectedToMaster() {
        SceneManager.LoadScene("Main");
    }
    //포톤 접속 종료시 로그인씬으로 이동합니다
    public override void OnDisconnected(DisconnectCause cause)
    {
        SceneManager.LoadScene(0);
    }
   
   // 로그인이 실패시 로그인을 다시 시도하라는 캔버스를 작동시킵니다.
    private void OnLoginFailure(PlayFabError error)
    {
        joinButton.interactable = true;
        failCanvas.gameObject.SetActive(true);
        isfade = true;
        
    }
    //로그인 실패시 작동하는 켄버스입니다. 캔버스그룹을 이용하여, 알파값을 조절해서 알파값이 0이되는 순간, 
    //캔버스를 끄고, 관련된 변수를 초기화합니다.
    void FadeOutCanvas(){
        if(timer < fadetime){
            timer += Time.deltaTime;
            failCanvas.alpha = Mathf.Lerp(1f, 0f, timer / fadetime);
        }
        else if ( timer >= fadetime){
            failCanvas.gameObject.SetActive(false);
            isfade = false;
            failCanvas.alpha = 1;
            timer = 0f;
        }
    }

    //회원가입에 성공하면 기존 로그인 캔버스를 가져옵니다.
    void OnRegisterSuccess(RegisterPlayFabUserResult result){
        loginMenuController.status = LoadingStatus.Main;
        loginMenuController.IsStatus();
    }

    //회원가입에 실패시 실패캔버스를 작동시킵니다.
    void OnRegisterFailure(PlayFabError error){
        failCanvas.gameObject.SetActive(true);
        isfade = true;
    }

	// 코인을 구매하거나 얻게될시 플레이팹의 통화를 증가시키고 최공값을 가져와 게임매니저값과 동기화합니다.
    public void AddCoin(int amount){
        var request = new AddUserVirtualCurrencyRequest(){ VirtualCurrency = "CO", Amount = amount};
        PlayFabClientAPI.AddUserVirtualCurrency(request, (result) => {
            GameManager.instance.userCoin = result.Balance;
            successCoinCanvas.gameObject.SetActive(true);
            mainAudioSource.clip = getCoinSound;
            mainAudioSource.Play();
        },
        (error) => Debug.Log("Coin Add Failed"));  
    }

	//코인을 사용할시 플래이팹 통화를 감소시키고 최종값을 가져와서, 게임매니저의 값과 동기화합니다.
    public void SubtractCoin(int amount)
    {
        var request = new SubtractUserVirtualCurrencyRequest(){VirtualCurrency = "CO", Amount = amount};
        PlayFabClientAPI.SubtractUserVirtualCurrency(request,(result) => GameManager.instance.userCoin = result.Balance, (error) => Debug.Log("Coin Subtract Failed"));
    }
}
```

### PlayerCharactor

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Photon.Pun;
using Photon.Realtime;

public class PlayerCharactor : MonoBehaviourPunCallbacks
{
    public int charactorSelectNumber;
    public GameObject[] bodyObject;
    public GameObject[] headObject;

    PhotonView pv;

    private void Awake() {
        pv = GetComponent<PhotonView>();
    }
    private void Start() {
        if(pv.IsMine){
			//지정한 캐릭터로 변경합니다.
            Invoke("ChooseCharactor",0.1f);
        }
    }

    //변경된 캐릭터를 모든 플레이어가 알아야하므로 PRC를 통해 동기화 해줍니다.
    [PunRPC]
    public void ChooseCharactor(){
		//메인화면에서 선택해둔 캐릭터값을 가지고있는 싱글톤 게임매니저에서 값을 가져옵니다.
        charactorSelectNumber = GameManager.instance.charactorSelectNumber;
        for(int i = 0; i < bodyObject.Length; i++){
            bodyObject[i].gameObject.SetActive(false);
            headObject[i].gameObject.SetActive(false);
        }
        bodyObject[charactorSelectNumber].gameObject.SetActive(true);
        headObject[charactorSelectNumber].gameObject.SetActive(true);
    }
}
```

### PlayerController

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.InputSystem;
using Photon.Pun;
using Photon.Realtime;
using Sirenix.OdinInspector;

public class PlayerController : MonoBehaviourPunCallbacks
{
    int mapSizeX;
    int mapSizeZ;
    float mapTileScale;
    public float moveSpeed;
    public float rotationSpeed;
    Rigidbody rig;
    Vector2 moveVec;
    public Transform shootPosition;
    public PhotonView pv;
    Vector3 curPos;
    Animator anim;

    public Bullets bullet;
    PlayerStatus playerStatus;
    bool isShootWeapon = false;

    private void Start() {
        anim = GetComponentInChildren<Animator>();
        playerStatus =  GetComponent<PlayerStatus>();
				
        //내가 소유권을 가진 캐릭터만 랜덤한 위치로 이동합니다. 
        if(pv.IsMine){
            rig = GetComponent<Rigidbody>();
            RandomPosition();
        }        
    }

    private void LateUpdate() {
        Move(); 
    }

    [Button]
    void RandomPosition(){
        if(pv.IsMine){
            mapSizeX = GameManager.instance.mapSizeX;
            mapSizeZ = GameManager.instance.mapSizeZ;
            mapTileScale = GameManager.instance.mapTileScale;

            float positionX = Random.Range(mapTileScale + 3, mapSizeX - mapTileScale - 3);
            float positionZ = Random.Range(mapTileScale + 3, mapSizeZ - mapTileScale - 3);
            Vector3 randomPosition = new Vector3(positionX, 1.5f, positionZ);
            transform.position = randomPosition;
        }
    }
		
    //내캐릭터의 위치값만 변동해줍니다. OnMoveInput을통해 inputsystem에서 입력값을 받아옵니다.
    void Move(){
        if(pv.IsMine){    
            Vector3 dir = Vector3.forward * moveVec.y + Vector3.right * moveVec.x;
            dir *= moveSpeed;
            dir.y = rig.velocity.y;
            rig.velocity = dir;

            if (moveVec != Vector2.zero)
            {
                transform.rotation = Quaternion.Lerp(transform.rotation, Quaternion.LookRotation(dir), Time.deltaTime * rotationSpeed);
            }
        }
    }
	
    //inputsystem에 의해 입력된값을 콜백 받으면, 지정된 애니메이션을 자동시키고, 콜랙받은 값을 변수에 전달합니다
    public void OnMoveInput(InputAction.CallbackContext context){
        if(context.phase == InputActionPhase.Performed){
            anim.SetBool("isMove", true);
            moveVec = context.ReadValue<Vector2>();
        }
        else if(context.phase == InputActionPhase.Canceled){
            anim.SetBool("isMove", false);
            moveVec = Vector2.zero;
        }
    }
	//inputsystem을 통해 콜백으로 값을 받으면, 사격애니메이션을 작동시키고, 총알프리팹을 생성합니다.
    public void OnAttackInput(InputAction.CallbackContext context){
        if(pv.IsMine){
            if(context.phase == InputActionPhase.Performed){
                anim.SetBool("isShoot",true);
                InvokeRepeating("ShootBullet", 0.1f, 0.1f); 
            } 
            else if(context.phase == InputActionPhase.Canceled){
                anim.SetBool("isShoot",false);
                CancelInvoke("ShootBullet");
            }
        }
    }
	//총알을 생성합니다. 포톤인스턴스를 이용하며, 총알을 생성할떄마다, 플레이어가 사진마나값을 소모하며, 마나가 0이면 생성된지 않습니다.
    public void ShootBullet(){
        if(playerStatus.mana.curValue >= bullet.manaDecoy){
            PhotonNetwork.Instantiate("Bullet" + bullet.bulletID, shootPosition.position , shootPosition.rotation);
            playerStatus.mana.Subtract(bullet.manaDecoy);
        } 
        Debug.Log("Bullet" + bullet.bulletID);
    }
}
```

### PlayerStatus

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using Photon.Pun;
using Photon.Realtime;

public class PlayerStatus : MonoBehaviourPunCallbacks, IDamagable
{
    public Status health;
    public Status mana;
    public PhotonView pv;
    float value;
    public Canvas endCanvas;
    public GameObject playerCharactor;

    private void Update() {
        statusUpdate();
        CheckHeight();
    }

    //계속회복되는 스테이터스와 플레이어 사망 유무를 계속판정합니다.
    public void statusUpdate(){
        CheckisPlayerDead();
        
        mana.Add(mana.regenRate * Time.deltaTime);
        CheckStatus();
    }

	//동기화된 Status를 ui바와 동기화합니다. 모든플레이어에게 동기화해줍니다.
    [PunRPC]
    void CheckStatus(){
        health.uiImage.fillAmount = health.GetPercent();
        mana.uiImage.fillAmount = mana.GetPercent();
    }

	//플레이어의 사망유무를 판정합니다.
    public void CheckisPlayerDead(){
        if(health.curValue == 0f){
            Die();
        }
    }

	//플레이어가 데미지를 받을시 작동합니다. 바뀐 스테이터스를 CheckStatus를 통해 동기화합니다.
    public void TakePhysicalDamage(int amount){
        health.Subtract(amount);
        pv.RPC("CheckStatus", RpcTarget.AllBuffered);
    }

	//플레이어가 사망했을때, 사망캔버스를 작동시킵니다.
    void Die(){
        Debug.Log( GameManager.instance.userName + "Die");
        endCanvas.gameObject.SetActive(true);
        playerCharactor.SetActive(false);
    }

	//플레이어가 일정높이 이하로 떨어졌을때, 사망한것으로 판정합니다.
    public void CheckHeight(){
        if(transform.position.y < -5){
            Die();
        }
    }
}

[System.Serializable]
public class Status
{
    public float curValue;
    public float maxValue;
    public float startValue;
    public float regenRate;
    public float decayRate;
    public Image uiImage;

    //스테이터스를 증가시킵니다. 맥스값이상으로 회복되는것을 방지합니다.
    public void Add(float amount){
        curValue = Mathf.Min(curValue + amount, maxValue);
    }

    //스테이터스를 감소시킵니다. 0값이하로 감소되는것을 방지합니다.
    public void Subtract(float amount){
        curValue = Mathf.Max(curValue - amount, 0);
    }

	//ui바와 동기화 하기위해 퍼센트값을 만들어줍니다.
    public float GetPercent(){
        return curValue / maxValue;
    }
    
}

//데미지를 받을때, 작동할 인터페이스입니다. 플레이어외에도 다양한 데미지를 받는 오브젝트에서 상속받아 사용합니다.
public interface IDamagable 
{
    void TakePhysicalDamage(int damageAmount);
}
```

### LoginMenuController

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Sirenix.OdinInspector;

//빠르고 간편하게 캔버스를 변경하기위해 지정해두었습니다.
public enum LoadingStatus{
    Main,
    SinginEmail,
    LoginEmail,
}

public class LoginMenuController : MonoBehaviour
{

    public Canvas loginCanvas;
    public Canvas emailLoginCanvas;
    public Canvas singinEmailCanvas;
    AudioSource audio;
    
    public LoadingStatus status;
   
    private void Start() {
		//프로그램 실행시 자동으로 메인캔버스를 열어줍니다.
        status = LoadingStatus.Main;
        audio = GetComponent<AudioSource>();
        IsStatus();
    }

    public void IsStatus(){
		// 모든 캔버스를 닫아줍니다.
        Reset();
		// status 상태에 따라, 지정된 캔버스만 작동해줍니다.
        switch (status){
            case LoadingStatus.Main : 
                loginCanvas.gameObject.SetActive(true);
                audio.Play();
            break;
            case LoadingStatus.LoginEmail : 
                emailLoginCanvas.gameObject.SetActive(true);
                audio.Play();

            break;
            case LoadingStatus.SinginEmail :
                singinEmailCanvas.gameObject.SetActive(true); 
                audio.Play();
            break;
            
        }
    }

	//모든캔버스를 안보이게합니다.
    void Reset(){
        loginCanvas.gameObject.SetActive(false);
        emailLoginCanvas.gameObject.SetActive(false);
        singinEmailCanvas.gameObject.SetActive(false);
    }

	//버튼과 동기화할 부분입니다. 버튼을 클릭할시 미리지정해준 0,1,2값이 들어오게되고, status 상태를 그 숫자에 맞게 바꾸게됩니다.
    public void OnButtonControll(int statusInt){
        int statusNum = statusInt;
        switch(statusNum){
            case 0 :
                status = LoadingStatus.Main;
                
            break;
            case 1 :
                status = LoadingStatus.LoginEmail;
            break;
            case 2 :
                status = LoadingStatus.SinginEmail;
            break;
        }
        IsStatus();
    }
}
```

### MainMenuController

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using UnityEngine.SceneManagement;
using TMPro;

//로긴메뉴컨트롤에 Ststus와 같은 이유입니다. 좀더 빠르고 편하게 캔버스를 관리하기위해 만들었습니다.
public enum UIStatus{
    Main,
    StartGame,
    CharactorSelect,
    Shop,
    Option
}

public class MainMenuController : MonoBehaviour
{
    [Header("Canvas")]
    public Canvas mainCanvas;
    public Canvas startGameCanvas;
    public Canvas charctorCanvas;
    public Canvas shopCanvas;
    public Canvas optionCanvas;
    public Canvas successCoinCanvas;

    [Header("Details")]
    public TextMeshProUGUI coinText;
    public Image charactorImage;
    public Sprite[] charactorSprites;
    public Sprite[] soundSprites;
    public int charactorSelectNumber;
    public PlayerCharactor game;
    public UIStatus status;
    public TextMeshProUGUI playerNameText;
    public Image soundImage;
    public Slider soundSilder;
    public TextMeshProUGUI soundText;
    public float soundSize = 1;
    public NetworkManager networkManager;
    AudioSource audioSource;

    private void Start() {
        audioSource = GetComponent<AudioSource>();
		//씬전환과 동시에 작동시키니 작동하지않아 약간의 텀을 주게합니다.
        Invoke("CheckBasic",1f);
    }

    public void IsStatus(){
		//모든 캔버스를 닫아줍니다.
        Reset();
		// status 상태에 따라, 지정된 캔버스만 작동해줍니다.
        switch (status){
            case UIStatus.Main : 
                mainCanvas.gameObject.SetActive(true);
                audioSource.Play();
            break;
            case UIStatus.StartGame : 
                startGameCanvas.gameObject.SetActive(true);
                audioSource.Play();
            break;
            case UIStatus.CharactorSelect :
                charctorCanvas.gameObject.SetActive(true);
                charactorSelectNumber = GameManager.instance.charactorSelectNumber;
                audioSource.Play();
            break;
            case UIStatus.Shop :
                shopCanvas.gameObject.SetActive(true);
                audioSource.Play();
            break;
            case UIStatus.Option :
                optionCanvas.gameObject.SetActive(true);
                audioSource.Play();
            break;
        }
    }
	
    // 모든 캔버스를 닫아줍니다.
    void Reset(){
        mainCanvas.gameObject.SetActive(false);
        startGameCanvas.gameObject.SetActive(false);
        charctorCanvas.gameObject.SetActive(false);
        shopCanvas.gameObject.SetActive(false);
        optionCanvas.gameObject.SetActive(false);

    }
	
    // 미리버튼에 특정 번호를 넣어주어서, 클릭시 자동으로 입력된 값에 맞게 stutus상태를 변경해줍니다.
    public void OnButtonControll(int statusInt){
        int statusNum = statusInt;
        switch(statusNum){
            case 0 :
                status = UIStatus.Main;
            break;
            case 1 :
                status = UIStatus.StartGame;
            break;
            case 2 :
                status = UIStatus.CharactorSelect;
            break;
            case 3 :
                status = UIStatus.Shop;
            break;
            case 4 :
                status = UIStatus.Option;
            break;
        }
        IsStatus();
    }

    // 플레이어 이름과 가지고있는 통화량을 보여줍니다.
    void CheckBasic(){
        playerNameText.text = GameManager.instance.userName;
        coinText.text = GameManager.instance.userCoin.ToString();
    }
      
    //클릭시 배틀로얄모드게임씬으로 로드합니다.
    public void OnBattleRoyaleMode(){
        networkManager.JoinRandomRoom();
    }

    //캐릭터선택창에서 오른쪽이동버튼입니다.
    public void OnRightChageButton(){
        if(charactorSelectNumber == charactorSprites.Length - 1){
            return;
        }
        charactorSelectNumber += 1;
        ChangeImage();
    }

    //캐릭터선택창에서 왼쪽이동버튼입니다.
    public void OnLeftChangeButton(){
        if(charactorSelectNumber == 0){
            return;
        }
        charactorSelectNumber -= 1;
        ChangeImage();
    }

    //캐릭터선택캔버스에서 이미지스프라이트를 변경해줍니다.
    void ChangeImage() => charactorImage.sprite = charactorSprites[charactorSelectNumber];

    //선택한 캐릭터를 게임매니저에 정보를 넘겨주고, 캐릭터선택캔버스을 꺼주고, 로비캔버스를 열어줍니다.
    public void OnSelectCharactorButton(){
        GameManager.instance.charactorSelectNumber = charactorSelectNumber;
        game.ChooseCharactor();
        OnButtonControll(0);
    }

    //코인을 얻고나면 구매에 성공햇다는 의미로 띄우는 UI창을 종료합니다.
    public void OnSuccessCoinButton(){
        successCoinCanvas.gameObject.SetActive(false);
        CheckBasic();
    }

    //슬라이더를 조정하면 바로 게임사운드를 조정합니다.
    //사운드가 0이되면 스프라이트를 자동으로 무음스프라이트로 교체하고 0이상이되면 다시 유음 스프라이트로 교체합니다.
    public void SoundValueCheck(){
        soundSize = soundSilder.value;
        soundText.text = Mathf.Ceil((soundSize * 100)).ToString();
        GameManager.instance.soundSize = soundSize;
        if(soundSize <= 0){
            GameManager.instance.isMute = true;
            soundImage.sprite = soundSprites[1];
        }
        else if(soundSize > 0){
            GameManager.instance.isMute = false;
            soundImage.sprite = soundSprites[0];
        }
        GameManager.instance.MuteSound();
        GameManager.instance.SoundChange();
    }

    //음소거 버튼을 눌렸을때 사운드를 무음으로 만들어줍니다.
    public void OnMuteButton(){
        if(GameManager.instance.isMute == false){
            GameManager.instance.isMute = true;
            soundImage.sprite = soundSprites[1];
        }
        else if(GameManager.instance.isMute == true){
            GameManager.instance.isMute = false;
            soundImage.sprite = soundSprites[0];
        }
        GameManager.instance.MuteSound();
    }
}
```

### PlayerHud

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;
using TMPro;
using Photon.Pun;
using Photon.Realtime;

//플레이어 HUD Ui와 관련된 스크립트입니다. 
public class PlayerHud : MonoBehaviourPunCallbacks
{
    public Transform player;
    public Canvas hudCanvas;
    public TextMeshProUGUI playerNameText;
    public Vector3 offset;
    public Vector3 roOffset;
    PlayerStatus status;
    public PhotonView pv;
    string playerName;

    private void Start() {
        ChangeName();
    }

    private void Update() {
		//UI 위치를 플레이어를 중심으로 지정합니다.
        transform.position = player.position + offset;
        transform.eulerAngles = roOffset;

    }

    public void ChangeName(){
		// 내가소유한 캐릭터라면 내 닉네임을 넣어주고, 색상을 흰색으로합니다.
        if(pv.IsMine){
            playerNameText.text = PhotonNetwork.NickName;
            playerNameText.color = Color.white;
        }
		// 다른플레이어가 소유한 캐릭터라면, 그 플레이어의 닉네임을 넣고, 생상을 붉은색으로합니다.
        else{
            playerNameText.text = photonView.Owner.NickName;
            playerNameText.color = Color.red;
        }
    }
}
```

### OdinDataTable

![Odin]({{ site.baseurl }}/images/TopDownKing/Odin.png)

```csharp
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEditor;
using Sirenix.OdinInspector;
using Sirenix.OdinInspector.Editor;
using Sirenix.Utilities.Editor;

public class OdinDataTable : OdinMenuEditorWindow
{
	//유니티 윈도우 메뉴에 메뉴 제작
    [MenuItem("Tools/DataTable")]
    private static void OpenWindow(){
        GetWindow<OdinDataTable>().Show();
    }

	//메뉴 내부 트리 작성.
    protected override OdinMenuTree BuildMenuTree()
    {
        var tree = new OdinMenuTree();
		//새로운 데이터 생성 Tree메뉴
        tree.Add("Create New Enemy", new CreateNewEnemyData());
		//만들어지거나, 만들어진 데이터들을 가져와서 테이블에 제공
        tree.AddAllAssetsAtPath("Item", "Assets/Resources", typeof(ItemData));

        return tree;
    }

		// 새로운 아이탬 데이터 생성
		public class CreateNewItemData{
        public CreateNewItemData(){
            itemData = ScriptableObject.CreateInstance<ItemData>(); 
            itemData.displayName = "New Item Data";
        }
        [InlineEditor(ObjectFieldMode = InlineEditorObjectFieldModes.Hidden)]
        public ItemData itemData;
		
        //오딘인스펙터 버튼, 새로운 데이터를 정해진 규칙에 따라 이름을 정하고 확장자를 정하고, 지정된 경로에 생성합니다.
        [Button("Add New Item")]
        private void CreateNewData(){
            AssetDatabase.CreateAsset(itemData, "Assets/Resources/" + itemData.displayName + ".asset");
            AssetDatabase.SaveAssets();

            itemData = ScriptableObject.CreateInstance<ItemData>(); 
            itemData.displayName = "New Item Data";
        }
    }}

```

## **Profile**

시뮬레이터모드로 iphone14max 기준으로 작동해서 측정했습니다.

전체적으로 버텍스가 많은 모델링 등이 없는 간단한 멀티FPS라서 큰문제가 없다생각했으나

로그인씬에서 로그인 과정 중 Memory leak이 일부 생겨있음을 확인했습니다.

### 1. Xcode Debug 네이게이터(CPU,Memory)

![Xcode4]({{ site.baseurl }}/images/TopDownKing/xcode4.png)

![03]({{ site.baseurl }}/images/TopDownKing/03.png)

### 2.Xcode CPU Profile

![Xcode5]({{ site.baseurl }}/images/TopDownKing/xcode5.png)

### 3.Xcode Profile Metal System Trace

![xcodeMetal]({{ site.baseurl }}/images/TopDownKing/xcodeMetal.png)

## **문제점 및 개선 방안**

1. 로긴화면에서 메인화면으로 전환시 바로 플레이어이름과 통화량이 적용되지않습니다 → 약간의 텀을주었습니다. 로딩화면을 만들예정입니다.
2. Max view id가 넘어가서 맵생성이 안되었습니다 → PhotonNetwork에서 최대값을 변경했습니다. 현재 맵이 너무 큰거 같아 다시 복구후 맵사이즈를 조정했습니다.

## **개선예정**

1. 다양한 아이탬 및 스킬을 제작하면 더 다양하게 즐길수 있을거같습니다.
2. 통화를 통해 캐릭터 락을 푸는 방식으로 통화를 사용할 거리를 만들어야겠습니다.
3. 상대방캐릭터가 동기화되는부분에서 문제가 있습니다.