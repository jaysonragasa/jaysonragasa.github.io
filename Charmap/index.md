![](https://raw.githubusercontent.com/jaysonragasa/Charmap/master/prev.gif)
  
# CharmapEx
Here's a simple **WPF Core** application called CharmapEx.
  
There's nothing really special to it other than you can load .TTF file or from the installed fonts in your system. You can select the character you want and will show you the code where you can use it in your XAML.

![](https://raw.githubusercontent.com/jaysonragasa/Charmap/master/Annotation%202020-05-03%20083835.png)

# Resource
You can grab your self some material font icons here.
* [https://materialdesignicons.com](https://materialdesignicons.com) 
* [https://icomoon.io/app](https://icomoon.io/app) - This is a great website where you can create a custom font, based from PNG files. All you have to do is to import the black and white icon .PNG files, select what you actually need, and let the website generate the .TTF file for you.

# Xamarin
Once you got the .TTF file. All you need to do is to copy that file in your main project. Like the screenshot below.  
  
![](https://raw.githubusercontent.com/jaysonragasa/Charmap/master/2020-05-03_1326.png)
  
And set the **Build Action** to **Embedded resource**
  
Open the `AssemblyInfo.cs` and add _(i.e. We have our materialdesignicons.ttf file)_ this line
  
```csharp
[assembly: ExportFont("materialdesignicons.ttf", Alias = "materialfonts")]
```
  
Now you can use your custom font like so
  
```xml
<Label Text=" &#xf039c; " FontFamily="materialfonts" />
```
This is how it looks  
  
![](https://raw.githubusercontent.com/jaysonragasa/Charmap/master/2020-05-03_1333.png)

# UWP
Well I'm trying to port this to UWP as well but .. I'm not sure if it is necessary. Anyhow, the UWP project is available when you check out the source code. The interface is there and requires an actual implementation that will work for UWP.
  
```csharp
public class Fonty : IFonty
{
    public List<Model_Character> CharacterLists { get => throw new NotImplementedException(); set => throw new NotImplementedException(); }
    public bool HasSelectedAFile { get => throw new NotImplementedException(); set => throw new NotImplementedException(); }
    public string SelectedFontFamilyName { get => throw new NotImplementedException(); set => throw new NotImplementedException(); }
    public object FontFamily { get => throw new NotImplementedException(); set => throw new NotImplementedException(); }

    public List<Model_Character> GetCharactersFromFontFamiy(object fontFamily)
    {
        throw new NotImplementedException();
    }

    public Task<List<object>> GetFontFamilies()
    {
        throw new NotImplementedException();
    }

    public Task<List<Model_Character>> Parse()
    {
        throw new NotImplementedException();
    }

    public void ShowOpenFileDialog()
    {
        throw new NotImplementedException();
    }
}
```

# AppCenter Release
You can download the WPF core app here  
[https://install.appcenter.ms/users/jaysondragasa-outlook.com/apps/charmapex/distribution_groups/public](https://install.appcenter.ms/users/jaysondragasa-outlook.com/apps/charmapex/distribution_groups/public)