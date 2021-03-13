# deit transformer on android . classification example
1. Run 
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ZackPashkin/deit-transformer-on-android-.-classification/blob/main/quantized_model_preparaion_transformer_deit.ipynb) to prepare model for android or download it from [here](https://storage.googleapis.com/clipnetgan/deit_tiny_android/fbdeit.pt)
2. Put model to assets folder
3. Build and run app

[<img src="https://github.com/ZackPashkin/deit-transformer-on-android-.-classification/blob/main/example_deit_classifier.gif" width="250"/>](https://github.com/ZackPashkin/deit-transformer-on-android-.-classification/blob/main/example_deit_classifier.gif)




## Gradle:app
```
apply plugin: 'com.android.application'

repositories {
    jcenter()
    maven {
        url "https://oss.sonatype.org/content/repositories/snapshots"
    }
}

android {
    compileOptions {
        sourceCompatibility 1.8
        targetCompatibility 1.8
    }
    compileSdkVersion 30
    defaultConfig {
        applicationId "org.pytorch.demo"
        minSdkVersion 21
        targetSdkVersion 30
        versionCode 1
        versionName "1.0"
        testInstrumentationRunner "androidx.test.runner.AndroidJUnitRunner"
        externalNativeBuild {
            cmake {
                cppFlags ""
                arguments "-DANDROID_STL=c++_shared"
            }
        }
        buildTypes {
            release {
                minifyEnabled false
                proguardFiles getDefaultProguardFile('proguard-android-optimize.txt'), 'proguard-rules.pro'
            }
        }
    }

    dependencies {
        implementation 'androidx.appcompat:appcompat:1.0.0-beta01'
        implementation 'androidx.constraintlayout:constraintlayout:1.1.3'

        def camerax_version = "1.0.0-alpha05"
        implementation "androidx.camera:camera-core:$camerax_version"
        implementation "androidx.camera:camera-camera2:$camerax_version"
        implementation 'com.google.android.material:material:1.0.0-beta01'

        implementation 'org.pytorch:pytorch_android:1.8.0-SNAPSHOT'
        implementation 'org.pytorch:pytorch_android_torchvision:1.8.0-SNAPSHOT'
    }
}

```
[!https://github.com/ZackPashkin/deit-transformer-on-android-.-classification/blob/main/gradle.png]

android studio version 4.1

# Reference
DEIT transformers repo
https://github.com/facebookresearch/deit

Pytorch mobile examples
https://github.com/pytorch/android-demo-app/tree/master/ViT4MNIST

Tutorial train mnist vit transformer
https://towardsdatascience.com/a-demonstration-of-using-vision-transformers-in-pytorch-mnist-handwritten-digit-recognition-407eafbc15b0

VIT transformer repo
https://github.com/lucidrains/vit-pytorch


