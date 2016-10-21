ShockWave Effect 
-------------------------------------
[Asset Store Link](http://u3d.as/oyN)  
© 2017 Justin Garza

PLEASE LEAVE A REVIEW OR RATE THE PACKAGE IF YOU FIND IT USEFUL!
Enjoy! :)

Contact  
-------------------------------------
Questions, suggestions, help needed?  
Contact me at:  
Email: jgarza9788@gmail.com  
Cell: 1-818-251-0647  
Contact Info: [justingarza.net/contact](http://justingarza.net/contact/)
  
Description/Features
-------------------------------------
Awesome ShockWave Effect!  * Add it to any script with just one line of code!
* Create ShockWaves (and Reverse ShockWaves)
* Customize your ShockWave style with AnimationCurves
* Easily Pause/UnPause Shockwaves
* Unity Free friendly.
* Fully commented C# code.
* Awesome demos!
Terms of Use
-------------------------------------
You are free to add this asset to any game you’d like
However:  
please put my name in the credits, or in the special thanks section. :)  
please do not re-distribute.  

Table of Contents 
-------------------------------------
1. ShockWave.cs
	* Speed,Radius,Amplitude,WaveSize
	* Methods
2. Demo1
3. Demo2
4. Demo3



ShockWave.cs 
-------------------------------------
ShockWave.cs is the main script that creates and manages the shockwaves. 

####Speed,Radius,Amplitude,WaveSize
these are the 4 values that we can adjust to change the look, and style of the shockwave.

**Speed:**  
this is just the speed at which the animation will play.

**Radius:**  
the distance between the center of the circle to it's edge. 

**Amplitude:**  
the distortion amount along the edge of the shockwave.

**WaveSize:**  
this is the thickness of the shockwave.

![Imgur](http://i.imgur.com/1gTOSQG.png?1)

####Methods

There are 12 methods that can be used to display a shockwave.

**This first set will allow you to pass in a Position (or a GameObject), and floats for Speed, MaxRadius, Amplitude, and WaveSize**

~~~cs
public void StartIt(Vector2 Position, float Speed = 1f,float MaxRadius = 1f, float Amplitude = 1f , float WaveSize = 0.2f) {...}
~~~

~~~cs
public void StartIt(Vector3 Position, float Speed = 1f,float MaxRadius = 1f, float Amplitude = 1f , float WaveSize = 0.2f) {...}
~~~

~~~cs
public void StartIt(Vector3 Position, bool IsScreenPosition, float Speed = 1f,float MaxRadius = 1f, float Amplitude = 1f , float WaveSize = 0.2f) {...}
~~~

~~~cs
public void StartIt(GameObject Target, float Speed = 1f,float MaxRadius = 1f, float Amplitude = 1f , float WaveSize = 0.2f) {...}
~~~

**Similar to the first set, this Second set will allow you to pass in a Position (or a GameObject), and floats for Speed, MaxRadius, Amplitude, and WaveSize.
However the animation will play in reverse**

~~~cs
public void ReverseIt(Vector2 Position, float Speed = 1f,float MaxRadius = 1f, float Amplitude = 1f , float WaveSize = 0.2f) {...}
~~~

~~~cs
public void ReverseIt(Vector3 Position, float Speed = 1f,float MaxRadius = 1f, float Amplitude = 1f , float WaveSize = 0.2f) {...}
~~~

~~~cs
public void ReverseIt(Vector3 Position, bool IsScreenPosition, float Speed = 1f,float MaxRadius = 1f, float Amplitude = 1f , float WaveSize = 0.2f) {...}
~~~

~~~cs
public void ReverseIt(GameObject Target, float Speed = 1f,float MaxRadius = 1f, float Amplitude = 1f , float WaveSize = 0.2f) {...}
~~~

**If you want more control over how the shockwave looks, the last set will allow you to pass in animationCurves**

~~~cs
public void StartIt(Vector2 Position, float Speed = 1f, AnimationCurve radiusOverTime =  null, AnimationCurve amplitudeOverTime = null , AnimationCurve waveSizeOverTime = null) {...}
~~~

~~~cs
public void StartIt(Vector3 Position, float Speed = 1f, AnimationCurve radiusOverTime =  null, AnimationCurve amplitudeOverTime = null , AnimationCurve waveSizeOverTime = null) {...}
~~~

~~~cs
public void StartIt(Vector3 Position, bool IsScreenPosition, float Speed = 1f, AnimationCurve radiusOverTime =  null, AnimationCurve amplitudeOverTime = null , AnimationCurve waveSizeOverTime = null) {...}
~~~

~~~cs
public void StartIt(GameObject Target, float Speed = 1f, AnimationCurve radiusOverTime =  null, AnimationCurve amplitudeOverTime = null , AnimationCurve waveSizeOverTime = null) {...}
~~~


Demo1 
-------------------------------------
In demo1 we are creating shockwaves based on the value of the sliders, and the value of the reverse toggle.

~~~cs  
...
	void Update () 
    {
        if (Input.GetMouseButtonDown(0))
        {
            if (RevSW)
            {
                ShockWave.Get().ReverseIt(Input.mousePosition,true,Speed,MaxRadius, Amp ,WS);
            }
            else
            {
                ShockWave.Get().StartIt(Input.mousePosition,true,Speed,MaxRadius, Amp, WS);
            }
        }
	}
...	
~~~


Demo2
-------------------------------------
In demo2 we are creating shockwaves not calling StartIt (or ReverseIt), and then setting the radius, amplitude, and waveSize to a random float.

This technique can be done if you want a lot of control over the shockwave, for example a game that uses 3D Touch.

~~~cs  
...
	void Update()
    {
        if (Input.GetMouseButtonDown(0))
        {
            
            SW = ShockWave.Get();
            SW.SetPosition(Input.mousePosition,true);
            SW.radius = Random.Range(0.05f,0.2f);
            SW.amplitude = Random.Range(0.05f,0.2f);
            SW.waveSize = Random.Range(0.05f,0.2f);

        }
    }
...
~~~


Demo3
-------------------------------------
Demo3 is a testing scene for the ShockWaves using AnimationCurves.
Edit the values in "ShockWaveMaker" GameObject, Play the scene, then click around.

~~~cs 
... 
	public float speed = 1f;
    public AnimationCurve radiusOverTime;
    public AnimationCurve amplitudeOverTime;
    public AnimationCurve waveSizeOverTime;

    void Update()
    {
        if (Input.GetMouseButtonDown(0))
        {
			ShockWave.Get().StartIt(Input.mousePosition,true,speed,radiusOverTime,amplitudeOverTime,waveSizeOverTime);
        }
    }
...    
~~~