![https://raw.githubusercontent.com/jaysonragasa/jaraimages/master/EvaluateCodeInXAML/2020-05-09_1825.png](https://raw.githubusercontent.com/jaysonragasa/jaraimages/master/EvaluateCodeInXAML/2020-05-09_1825.png)

## Basic Information
I couldn't think of any best example of this one so above is a little example how you can execute/evaluate a code inside the XAML file. 
  
There are three things happening here  
1. The placeholder hides when there's an image.
2. The placeholder shows when there is no image.
3. It shows a portion of the item name inside the placeholder.
  
I know, I know. Coverters can easily do this. You just have to create a Converter for hiding a part of an element and a Converter for taking part of the string... but this is a code inside the XAML and one great thing with this one is for example in Hot Reload, you will be able to see the changes. Imagine the flexibility of having an inline code inside the XAML.
  
So if you notice, I am only using one converter `eval` which executes my code.
  
**Here's GIF preview**
  
![https://raw.githubusercontent.com/jaysonragasa/jaraimages/master/EvaluateCodeInXAML/05-07-2020-15-01-59.gif](https://raw.githubusercontent.com/jaysonragasa/jaraimages/master/EvaluateCodeInXAML/05-07-2020-15-01-59.gif)
  
  
## History
This is made possible by [Interpreter](https://github.com/jaysonragasa/Interpreter) made by [HiSystems](https://github.com/hisystems) way back 2013. The development was stopped last 2015 and I think this is a good addition to Xamarin platform, WPF, or UWP.
  
I extended the Interpreter a bit to support some additional functions. Check [README](https://github.com/jaysonragasa/Interpreter/blob/master/readme.md)
  
## So why Converter?
I was trying to implement this with Attached Attribute to somehow make it a bit interesting but I want this to run in any attributes in element.
  
I also tried using Markup Extension but it's just not possible since the source path could be in any name and it is important to know the source and getting the source value is even harder.
  
So the Converter is much easier to implement. It can be implemented in any attributes and you can easily get the actual value from the source.
  
Here's our converter
```csharp
public class Convert_Interpret : IValueConverter
{
    public object Convert(object value, Type targetType, object parameter, CultureInfo culture)
    {
        object result = null;

        if (!string.IsNullOrEmpty((string)value))
        {
            string p = (string)parameter;
            p = p.Trim();

            var e = ((App)Application.Current).Interpret;
            var xp = e.Parse(p);
            xp.Variables["x"].Value = new Text((string)value);
            return xp.Execute();
        }

        return result;
    }

    public object ConvertBack(object value, Type targetType, object parameter, CultureInfo culture)
    {
        return value;
    }
}
```
  
Added this line in App.xaml.cs
```csharp
public Engine Interpret = new Engine();
```