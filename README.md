PopupCircleMenu
=====================
模仿花瓣APP的弹出式菜单
---------------------
点击查看 [演示](https://github.com/panshen/PopupCircleMenu/blob/master/preview.gif)

### Gradle
```

	allprojects {
		repositories {
			maven { 
			    url 'https://jitpack.io' 
			}
		}
	}


	dependencies {
		compile 'com.github.panshen:PopupCircleMenu:v0.1'
	}
	
```

### Usage

```
 PopupCircleView ppView;
        .....
        //按钮被选中的回调
         ppView.setmOnMenuEventListener(new PopupCircleView.OnMenuEventListener() {
            @Override
            public void onMenuToggle(PopupButton popupButton, int index) {
                if (popupButton.getId() == R.id.pb_fav) {
                    if(popupButton.isChecked()){
                         Toast.makeText(MainActivity.this, "收藏", Toast.LENGTH_SHORT).show();
                    }else {
                       Toast.makeText(MainActivity.this, "取消收藏", Toast.LENGTH_SHORT).show();
                    }
                } 
            }
        });
        
        //按钮可用时的回调
            ppView.setOnButtonPreparedListener(new PopupCircleView.OnButtonPreparedListener() {
                @Override
                public void onPrepared(ArrayList<PopupButton> bts) {
                    for (PopupButton pb : bts) {
                        if (bean.isLike())
                            if (pb.getId() == R.id.pb_like) {
                                pb.setChecked(true);
                            }
                    }
                }
            });
 
 
```

#在XML中添加
```

<com.panshen.xps.popupcirclemenu.PopupCircleView
            android:id="@+id/PopupMenu_dot"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_gravity="center_horizontal"
            app:anim_duration="300"
            app:open_direction="RIGHT"
            app:radius="100dp">
            
            
             <com.panshen.xps.popupcirclemenu.PopupButton
                android:layout_width="55dp"
                android:layout_height="55dp"
                app:pb_color="#ffffff"
                app:pb_color_checked="#FFEBEBEB" />

            <com.panshen.xps.popupcirclemenu.PopupButton
                android:id="@+id/pb_like_dot"
                android:layout_width="55dp"
                android:layout_height="55dp"
                app:pb_background="@drawable/tv"
                app:pb_color="#ffffff"
                app:pb_checkable="true"
                app:pb_color_checked="#57c8e2" />

            ...
            ...

            
            <ImageView
                android:id="@+id/iv_dot"
                android:layout_width="55dp"
                android:layout_height="55dp"
                android:padding="12dp"
                android:src="@drawable/dots" />

        </com.panshen.xps.popupcirclemenu.PopupCircleView>
```
        
        
 ```
        

public interface OnMenuEventListener {
        /**
         *
         * @param  popupButton 被触发的按钮
         * @param index 被触发按钮的index
         * */
        void onMenuToggle(PopupButton popupButton, int index);
    }
    
   
public interface OnButtonPreparedListener {
        /**   
         * 当按钮可用时回调
         * @param bts 按钮对象List
         * */
        void onPrepared(ArrayList<PopupButton> bts);
    }
    
```

### Note:


>PopupCircleView 里的第一个PopupButton作为中心按钮 可以不放图片资源

>PopupCircleView 在被单击时会触发最后一个View的onClick()


 

### Attributes
#PopupCircleView 



name | format | description 
--- |----------| ---
 radius        | dimension     |  菜单的半径  |
 anim_duration | integer       |  菜单动画的时间 |
 open_direction| enum          |  固定菜单展开的方向 |

#PopupButton 
  name          | format      | description 
 ------------- |-------------| -----
 pb_color      | color/reference | 按钮的颜色 
 pb_color_checked| color/reference      |  按钮被选中时的颜色 
 pb_background | reference      |     按钮的图片 
 pb_background_checked | reference      |     按钮被选中时的图片 
 pb_checkable      | boolean | 是否可被选中(默认false) 



