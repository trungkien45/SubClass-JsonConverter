# SubClass-JsonConverter
SubClass JsonConverter

```csharp
Interface1 interface1 = new Class1 {
    Class1Property1 = "", Class1Property2 = "",
    Class1Property3 = "",
    Interface1Property1 = "",
    Interface1Property2 = "",
    Interface1Property3 = ""
};

JsonSerializerOptions options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
    //Converters = { new SubClassConverter() },
    DefaultIgnoreCondition = JsonIgnoreCondition.WhenWritingDefault,
    WriteIndented = true,
};
var x1 = JsonSerializer.Serialize(interface1, typeof(Interface1), options);
Console.WriteLine(x1);
// result when not using converter
/*
{
  "Interface1Property1": "",
  "Interface1Property2": "",
  "Interface1Property3": ""
}
 */


JsonSerializerOptions options1 = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
    Converters = { new SubClassJsonConverter() },
    DefaultIgnoreCondition = JsonIgnoreCondition.WhenWritingDefault,
    WriteIndented = true,
};
var x15 = JsonSerializer.Serialize(interface1, typeof(Interface1), options1);
Console.WriteLine(x15);
// result when using converter
/*
{
  "Interface1Property1": "",
  "Interface1Property2": "",
  "Interface1Property3": "",
  "Class1Property1": "",
  "Class1Property2": "",
  "Class1Property3": ""
}
 */
'''
