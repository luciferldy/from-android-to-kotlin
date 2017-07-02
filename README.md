# From Android To Kotlin

> From Android To Kotlin - Easy to use Kotlin in Andorid



> Java

```java
public class SampleActivity extends AppCompatActivity {
  public SampleAcitivity() {
    // constructor
    ...
  }
  
  @Override
  public class onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    ...
  }
}
```

> Kotlin

```kotlin
class SampleActivity: AppCompatActivity {
	init {
      // constructor
      ...
	}
	
	override fun onCreate(savedInstanceState: Bundle?) {
      super.onCreate(savedInstanceState);
	}
}
```



---

> Java

```java
class SimpleOnClickListener implements View.OnClickListener {
  @Override
  public void onClick(View view) {

  }
}
```

> Kotlin

```kotlin
class SimpleOnClickListener : View.OnClickListener {
  override fun onClick(v: View?) {
  }
}
```



---

> Java

```java
public class Singleton {
  private static Singleton instance;
  private Singleton() {}
  public static Singleton getInstance(){
    if (instance == null ) {
      instance = new Singleton();
    }
    return instance;
  }
  
}
```

>Kotlin

```kotlin
class Singleton private constructor() {
  init { 
    ...
  }
  // 经过测试不需要 Holder 做延迟，另外 lazy 是线程安全的，不需要额外的加锁
  //private object Holder {
  //  val INSTANCE = Singleton()
  //}
  companion object {
    val instance: Singleton by lazy {
      //Holder.INSTANCE
      ...
      Singleton()
    }
  }
}
```

Or

```koltin
class Singleton private construtor() {
  init {
    ...
  }
  companion object {
    val instance = Singleton()
  }
}
```



---

> Java

```java
TextView tv = (TextView) findViewById(R.id.tv);
tv.setTextSize(48);
tv.setTextColor(getResouces().getColor(R.color.black));
tv.setText("Java");
```

> Kotlin

```kotlin
val tv: TextView = findViewById(R.id.tv) as TextView
with(tv){
  setTextSize(48)
  setColor(resources.getColor(R.color.black))
  setText("Java")
}
```



----

> Java

```java
public class SampleActivity extend AppCompatActivity {
  @Override
  public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    Button btn = (Button) findViewById(R.id.btn);
    btn.setOnClickListener(new OnClickListener {
      SampleActivity.this.onClick();
    });
  }
  
  private void onClick() {}
}
```

> Kotlin

```kotlin
class SampleActivity : AppCompatActivty() {
  override onCreate(savedInstanceState: Bundle?) {
    super.onCreate(savedInstanceState)
    val btn = findViewById(R.id.btn) as Button
    btn.setOnClickListener {
      v ->
      this@SampleActivity.onClick()
    }
  }
  
  private fun onClick() {}
}
```

