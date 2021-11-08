To use this you should add this repo to your project
```
allprojects {
    repositories {
        ...
        maven { url 'https://github.com/PayamVahedi/card-scanner/raw/master' }
    }
}
```

and then you can use the dependency:

```
dependencies {
    ...
    implementation 'com.hamrasta:cardscanner:+'
}
```

The minimum sdk version of this library is 19.
After adding the dependency you should call init function of CardScannerActivity:

```
    

    @Override
        protected void onCreate(Bundle savedInstanceState) {
            super.onCreate(savedInstanceState);
            setContentView(R.layout.activity_main);

            CardScannerActivity.init(apiKey, apiSecret);
            // then you can use the activity
            
            Button button = findViewById(R.id.scanbtn);
            button.setOnClickListener(new View.OnClickListener() {
                @Override
                public void onClick(View view) {
                    startActivityForResult(new Intent(MainActivity.this, CardScannerActivity.class), 0);
                }
            });
    
        }


    @Override
        protected void onActivityResult(int requestCode, int resultCode, @Nullable Intent data) {
            super.onActivityResult(requestCode, resultCode, data);
            if (requestCode == 0) {
                if (resultCode == RESULT_OK) {
                    if (data != null) {
                        String pan = data.getStringExtra("pan");
                        // do whatever you want with the pan
                    }
                }
            }
        }
```

