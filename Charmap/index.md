![](https://raw.githubusercontent.com/jaysonragasa/Charmap/master/prev.gif)
  
# Charmap
Here's a simple Charmap written in **WPF Core 3.1**.  
  
There's nothing really special to it but you can load .TTF file or fron the installed fonts in your system. You can select the character you want and will show you the code where you can use it in your XAML.

# UWP
Well I'm trying to port this to UWP as well but .. I'm not sure it's necessary. UWP project is available when you check out the soure code. The interface is there and requires implementation that will work for UWP.
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