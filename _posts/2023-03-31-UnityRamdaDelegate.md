---
layout: post
title:  Unity 델리게이트 람다식
date:   2023-03-31
image: Unity/cat003.jpeg
tags: Unity
---

---
## Unity 델리게이트, 람다함수
---


1. 델리게이트 : 일명 대리자라하여, 같은형식과 같은 인자를 쓰는 함수를 대신해서 쓰일수 있습니다. 다양한 활용이 가능할거같으나, 아직 활용을 잘못하고있습니다.<br> 
사실 개인적으로는 그함수를 쓰거나 굳이 여러함수를 델리게이트 함수 하나로 여러함수를 대처 할 때 어떤함수를 델리게이트에 넣을지 결정하는 과정이 필요할때, 결국 아직 전 if나 swith를 사용하게되고, 이렇게 되면 굳이 델리게이트 함수를 쓸 필요가 없는 경우가 많았습니다.

선언은 클래스 내나 외부 어디서 해도 상관없이 땡겨서 사용할수 있었습니다

2. 람다함수 : 사실 람다함수는 여러 형태가 존재합니다. 익명함수처럼 이름이 없고, 즉석에서 매게변수많을 통해 만드는 것입니다.<br>
즉, (변수) => {함수식;}; 형식이지만,
Only assignment, call, increment, decrement, await, and new object expressions can be used as a statement 오류를 볼수 있을것입니다.

하지만, 일반함수를 람다식으로 표현하는 부분은 잘작동합니다. 한줄정도의 짧은 함수를 작성할때는 자주 사용할수있습니다.

```c#
   public int damage;
   public int maxDamage;
   public int minDamage;
   public float damageRate;
   
   public TextMeshProUGUI critical;

   //델리게이트 선언
   public delegate void criticalPopup (int damage);

   List<IDamagable> thingsToDamage = new List<IDamagable>(); 

   // 람다식으로 바꾼 함수 , 사실 적어야 하는 부분이 더있지만, 일단 지웠습니다. 
   public void normal(int damage) => critical.text = damage.ToString(); 
   public void max(int damage) {
      critical.text = damage.ToString();
      critical.fontSize = 150;
      critical.fontStyle = FontStyles.Bold;

   IEnumerator Damage () {
   while(true){
      for(int i = 0; i < thingsToDamage.Count; i++){
            damage = Random.Range(minDamage, maxDamage+1);
            criticalPopup message;
            
            if(damage == maxDamage){
               message = max;
               message(damage);
            }
            else{
               message = normal;
               message(damage);
            }
            thingsToDamage[i].TakePhysicalDamage(damage);      
      }
      yield return new WaitForSeconds(damageRate);
   }
}
      
   }
```

위의 스크립트는 개인프로젝트 스크립트중 일부를 바꾼 것입니다.<br>
 <mark style='background-color: #dcffe4'>criticalPopup</mark>을 델리게이트로 선언해주었으며, 델리게이트를 <mark style='background-color: #dcffe4'>사용할 max와 min 함수</mark>가 존재합니다.<br>
 
두개의 함수는 damege를 주는 과정에서 damage가 랜덤하게 나올 때,<br>
maxdamage와 damage가 같은 수이면, 델리게이트는 max함수를 받아쓰게되고, 그외의 경우는 min을 받아주게됩니다.<br> 
사실 명확히 그걸 보여주기 위해 else를 작성했지만, message라는 델리게이트 변수를 선언해줄때 min으로 바로 받아주게되면 else는 필요없습니다.
