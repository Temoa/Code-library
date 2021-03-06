# Android 动画

## 视图动画

* AlphaAnimation 渐变
* RotateAnimation 旋转
* TranslateAnimation 平移
* ScaleAnimation 伸缩


* alpha
* rotate
* translate
* scale

在Java 中设置视图动画

```java
AlphaAnimation aa = new AlphaAnimation(0, 1);
aa.setDuration(1000);
view.startAnimation(aa);

RotateAnimation ra = new RotateAnimation(0, 360, 100, 100);
// 参数分别是起始角度和旋转的中心. 如果是view 自身的旋转中心参考以下
RotateAnimation ra2 = new RotateAnimation(0, 360,
    Animation.RELATIVE_TO_SELF, 0.5, 
    Animation.RELATIVE_TO_SELF, 0.5);

TranslateAnimation ta = new TranslateAnimation(0, 200, 0, 300);

ScaleAnimation sa = new ScaleAnimation(0, 2, 0, 2);
// 参数: 前面两个参数是x 轴方向的伸缩, 后面则为y 轴反向
// 和RotateAnimation 一样可以设置以view 自身为伸缩中心
ScaleAnimation sa2 = new ScaleAnimation(0, 1, 0, 1
    Animation.RELATIVE_TO_SELF, 0.5, 
    Animation.RELATIVE_TO_SELF, 0.5);
```

在XML 中设置动画

```xml
<set xmlns:android="http://schemas.android.com/apk/res/android" >
    <alpha
        android:fromAlpha="0.1"
        android:toAlpha="1.0"
        android:duration="3000"
    />
</set>
<!-- 透明度控制动画效果 alpha
        浮点型值：
            fromAlpha 属性为动画起始时透明度
            toAlpha   属性为动画结束时透明度
            说明: 
                0.0表示完全透明
                1.0表示完全不透明
            以上值取0.0-1.0之间的float数据类型的数字
        
        长整型值：
            duration  属性为动画持续时间
            说明:     
                时间以毫秒为单位
-->

<set xmlns:android="http://schemas.android.com/apk/res/android">
   <scale  
          android:interpolator="@android:anim/accelerate_decelerate_interpolator"
          android:fromXScale="0.0"
          android:toXScale="1.4"
          android:fromYScale="0.0"
          android:toYScale="1.4"
          android:pivotX="50%"
          android:pivotY="50%"
          android:fillAfter="false"
          android:duration="700" />
</set>
<!-- 尺寸伸缩动画效果 scale
       属性：interpolator 指定一个动画的插入器
        在我试验过程中，使用android.res.anim中的资源时候发现
        有三种动画插入器:
            accelerate_decelerate_interpolator  加速-减速 动画插入器
            accelerate_interpolator        加速-动画插入器
            decelerate_interpolator        减速- 动画插入器
        其他的属于特定的动画效果
      浮点型值：
         
            fromXScale 属性为动画起始时 X坐标上的伸缩尺寸    
            toXScale   属性为动画结束时 X坐标上的伸缩尺寸     
        
            fromYScale 属性为动画起始时Y坐标上的伸缩尺寸    
            toYScale   属性为动画结束时Y坐标上的伸缩尺寸    
        
            说明:
                 以上四种属性值    
    
                    0.0表示收缩到没有 
                    1.0表示正常无伸缩     
                    值小于1.0表示收缩  
                    值大于1.0表示放大
        
            pivotX     属性为动画相对于物件的X坐标的开始位置
            pivotY     属性为动画相对于物件的Y坐标的开始位置
        
            说明:
                    以上两个属性值 从0%-100%中取值
                    50%为物件的X或Y方向坐标上的中点位置
        
        长整型值：
            duration  属性为动画持续时间
            说明:   时间以毫秒为单位

        布尔型值:
            fillAfter 属性 当设置为true ，该动画转化在动画结束后被应用
-->

<set xmlns:android="http://schemas.android.com/apk/res/android">
    <translate
        android:fromXDelta="30"
        android:toXDelta="-80"
        android:fromYDelta="30"
        android:toYDelta="300"
        android:duration="2000"
    />
</set>
<!-- translate 位置转移动画效果
        整型值:
            fromXDelta 属性为动画起始时 X坐标上的位置    
            toXDelta   属性为动画结束时 X坐标上的位置
            fromYDelta 属性为动画起始时 Y坐标上的位置
            toYDelta   属性为动画结束时 Y坐标上的位置
            注意:
                     没有指定fromXType toXType fromYType toYType 时候，
                     默认是以自己为相对参照物             
        长整型值：
            duration  属性为动画持续时间
            说明:   时间以毫秒为单位
-->

<set xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate 
        android:interpolator="@android:anim/accelerate_decelerate_interpolator"
        android:fromDegrees="0" 
        android:toDegrees="+350"         
        android:pivotX="50%" 
        android:pivotY="50%"     
        android:duration="3000" />  
</set>
<!-- rotate 旋转动画效果
       属性：interpolator 指定一个动画的插入器
             在我试验过程中，使用android.res.anim中的资源时候发现
             有三种动画插入器:
                accelerate_decelerate_interpolator   加速-减速 动画插入器
                accelerate_interpolator               加速-动画插入器
                decelerate_interpolator               减速- 动画插入器
             其他的属于特定的动画效果
                           
       浮点数型值:
            fromDegrees 属性为动画起始时物件的角度    
            toDegrees   属性为动画结束时物件旋转的角度 可以大于360度   

        
            说明:
                     当角度为负数——表示逆时针旋转
                     当角度为正数——表示顺时针旋转              
                     (负数from——to正数:顺时针旋转)   
                     (负数from——to负数:逆时针旋转) 
                     (正数from——to正数:顺时针旋转) 
                     (正数from——to负数:逆时针旋转)       

            pivotX     属性为动画相对于物件的X坐标的开始位置
            pivotY     属性为动画相对于物件的Y坐标的开始位置
                
            说明:        以上两个属性值 从0%-100%中取值
                         50%为物件的X或Y方向坐标上的中点位置

        长整型值：
            duration  属性为动画持续时间
            说明:       时间以毫秒为单位
-->
```

使用XMl 中的动画

```java
Animation anim = AnimationUtils.loadAnimation(context, R.anim.my_animation);
```

动画集合AnimationSet, 将动画以组合的方式展示出来

```java
AnimationSet as = new AnimationSet(true);
as.setDuration(1000);

AlphaAnimation aa = new AlphaAnimation(0, 1);
aa.setDuration(1000);
as.addAnimation(aa);

TranslateAnimation ta = new TranslateAnimation(0, 100, 0, 200);
ta.setDuration(1000);
as.addAnimation(ta);

view.startAnimation(as);
```

动画监听

```java
animation.setAnimationListener(new Animation.AnimationListener() {

    @Override
    public void onAnimationStart(Animation animation) {

    }

    @Override
    public void onAnimationEnd(Animation animation) {
        
    }

    @Override
    public void onAnimationRepeat(Animation animation) {
        
    }
})
```