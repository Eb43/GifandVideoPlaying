# Gif and Video Playing
Android app displays embedded animated GIF and plays embedded MP4 video after the button press. For video preview a frame on its 1 ms is shown.
<br>
<img alt="fireworks imitation on android" src="https://raw.githubusercontent.com/Eb43/GifandVideoPlaying/main/GifandVideoPlaying.gif" style="width:300px;"/>

The GIF is locatd in res/drawable/img.gif
The video is locatd in res/raw/video.mp4

APK link
https://github.com/Eb43/GifandVideoPlaying/blob/main/GifandVideoPlaying.apk

## Notes

Android needs additional libraries to be used to display animated GIF. The GIF is loaded into the ImageView using Glide

```
        ImageView prebuiltImage = findViewById(R.id.prebuiltImage);
        Glide.with(this)
                .asGif()
                .load(R.drawable.img) // Ensure img.gif is placed in the res/drawable folder
                .into(prebuiltImage);
```

In /app/build.gradle.kts the dependencies block should include Glide libraries

```
dependencies {
    implementation(libs.appcompat)
    implementation(libs.material)
    implementation(libs.glide)
    annotationProcessor(libs.glideCompiler)
    testImplementation(libs.junit)
    androidTestImplementation(libs.extJunit)
    androidTestImplementation(libs.espressoCore)
}
```

Such notation of the dependencies requires the dependencies to be specified in /gradle/libs.versions.toml

```
[versions]
agp = "8.3.0"
junitVersion = "1.2.1"

appcompat = "1.6.1"
material = "1.9.0"
glide = "4.15.1"
glideCompiler = "4.15.1"
junit = "4.13.2"
extJunit = "1.1.5"
espressoCore = "3.5.1"


[libraries]
appcompat = { module = "androidx.appcompat:appcompat", version.ref = "appcompat" }
material = { module = "com.google.android.material:material", version.ref = "material" }
glide = { module = "com.github.bumptech.glide:glide", version.ref = "glide" }
glideCompiler = { module = "com.github.bumptech.glide:compiler", version.ref = "glideCompiler" }
junit = { module = "junit:junit", version.ref = "junit" }
extJunit = { module = "androidx.test.ext:junit", version.ref = "extJunit" }
espressoCore = { module = "androidx.test.espresso:espresso-core", version.ref = "espressoCore" }


[plugins]
androidApplication = { id = "com.android.application", version = "8.0.2" }

```
