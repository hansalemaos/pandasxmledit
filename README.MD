# simplifies working with XML data by leveraging the power and flexibility of pandas DataFrames

## Tested against Windows 10 / Python 3.11 / Anaconda

### pip install pandasxmledit


## Effortlessly Manipulate XML Data with Pandas DataFrames

pandasxmledit is a Python library that simplifies the process of working with XML data by providing an intuitive interface through pandas DataFrames. 
It allows you to easily load, edit, and save XML data, all within the familiar pandas ecosystem. 
Whether you're a data scientist, data analyst, or software developer, PandasXMLEdit streamlines XML data processing and empowers you to work more efficiently.

## Key Features

### Seamless Integration: 

Leverage the power of pandas to manipulate and analyze XML data effortlessly. Integrate XML data processing seamlessly into your data workflows.

### Automatic Data Type Conversion: 

Optionally, automatically convert XML values to their appropriate data types, simplifying data transformation tasks.

### Data Filtering and Modification: 

Filter, update, and manipulate XML data with ease using DataFrame operations. Apply calculations and transformations to specific elements.

### XML Data Serialization: 

Update the original XML data with changes made to the DataFrame and save the updated XML to a file.

### Error Handling: 

Built-in error handling ensures robust XML data processing from various sources, including URLs and local files.

```python
# Create a PandasXMLEdit instance with XML data from a URL
from pandasxmledit import PandasXMLEdit
xmledit = PandasXMLEdit(
	xmldata="https://github.com/hansalemaos/screenshots/raw/main/xmlexample.xml",
	convert_dtypes=True,
	process_namespaces=False,
)

# Modify values in the DataFrame
xmledit.df.loc[xmledit.df.key_3 == 'author', 'value'] = 'Stephen King'
xmledit.df.loc[xmledit.df.key_3 == 'price', 'value'] *= 10

# Update the XML data with DataFrame changes
xmledit.update_xml_data(pretty=True)

# Display the updated XML data and its dictionary representation
print(xmledit.xmldata)
print(xmledit.xmldict)

# Save the updated XML data to a file
xmledit.save_xml(r"c:\updatedxml.xml")
```


### Original XML 


```xml 
<?xml version="1.0"?>
<catalog>
   <book id="bk101">
      <author>Gambardella, Matthew</author>
      <title>XML Developer's Guide</title>
      <genre>Computer</genre>
      <price>44.95</price>
      <publish_date>2000-10-01</publish_date>
      <description>An in-depth look at creating applications 
      with XML.</description>
   </book>
   <book id="bk102">
      <author>Ralls, Kim</author>
      <title>Midnight Rain</title>
      <genre>Fantasy</genre>
      <price>5.95</price>
      <publish_date>2000-12-16</publish_date>
      <description>A former architect battles corporate zombies, 
      an evil sorceress, and her own childhood to become queen 
      of the world.</description>
   </book>
   <book id="bk103">
      <author>Corets, Eva</author>
      <title>Maeve Ascendant</title>
      <genre>Fantasy</genre>
      <price>5.95</price>
      <publish_date>2000-11-17</publish_date>
      <description>After the collapse of a nanotechnology 
      society in England, the young survivors lay the 
      foundation for a new society.</description>
   </book>
   <book id="bk104">
      <author>Corets, Eva</author>
      <title>Oberon's Legacy</title>
      <genre>Fantasy</genre>
      <price>5.95</price>
      <publish_date>2001-03-10</publish_date>
      <description>In post-apocalypse England, the mysterious 
      agent known only as Oberon helps to create a new life 
      for the inhabitants of London. Sequel to Maeve 
      Ascendant.</description>
   </book>
   <book id="bk105">
      <author>Corets, Eva</author>
      <title>The Sundered Grail</title>
      <genre>Fantasy</genre>
      <price>5.95</price>
      <publish_date>2001-09-10</publish_date>
      <description>The two daughters of Maeve, half-sisters, 
      battle one another for control of England. Sequel to 
      Oberon's Legacy.</description>
   </book>
   <book id="bk106">
      <author>Randall, Cynthia</author>
      <title>Lover Birds</title>
      <genre>Romance</genre>
      <price>4.95</price>
      <publish_date>2000-09-02</publish_date>
      <description>When Carla meets Paul at an ornithology 
      conference, tempers fly as feathers get ruffled.</description>
   </book>
   <book id="bk107">
      <author>Thurman, Paula</author>
      <title>Splish Splash</title>
      <genre>Romance</genre>
      <price>4.95</price>
      <publish_date>2000-11-02</publish_date>
      <description>A deep sea diver finds true love twenty 
      thousand leagues beneath the sea.</description>
   </book>
   <book id="bk108">
      <author>Knorr, Stefan</author>
      <title>Creepy Crawlies</title>
      <genre>Horror</genre>
      <price>4.95</price>
      <publish_date>2000-12-06</publish_date>
      <description>An anthology of horror stories about roaches,
      centipedes, scorpions  and other insects.</description>
   </book>
   <book id="bk109">
      <author>Kress, Peter</author>
      <title>Paradox Lost</title>
      <genre>Science Fiction</genre>
      <price>6.95</price>
      <publish_date>2000-11-02</publish_date>
      <description>After an inadvertant trip through a Heisenberg
      Uncertainty Device, James Salway discovers the problems 
      of being quantum.</description>
   </book>
   <book id="bk110">
      <author>O'Brien, Tim</author>
      <title>Microsoft .NET: The Programming Bible</title>
      <genre>Computer</genre>
      <price>36.95</price>
      <publish_date>2000-12-09</publish_date>
      <description>Microsoft's .NET initiative is explored in 
      detail in this deep programmer's reference.</description>
   </book>
   <book id="bk111">
      <author>O'Brien, Tim</author>
      <title>MSXML3: A Comprehensive Guide</title>
      <genre>Computer</genre>
      <price>36.95</price>
      <publish_date>2000-12-01</publish_date>
      <description>The Microsoft MSXML3 parser is covered in 
      detail, with attention to XML DOM interfaces, XSLT processing, 
      SAX and more.</description>
   </book>
   <book id="bk112">
      <author>Galos, Mike</author>
      <title>Visual Studio 7: A Comprehensive Guide</title>
      <genre>Computer</genre>
      <price>49.95</price>
      <publish_date>2001-04-16</publish_date>
      <description>Microsoft Visual Studio 7 is explored in depth,
      looking at how Visual Basic, Visual C++, C#, and ASP+ are 
      integrated into a comprehensive development 
      environment.</description>
   </book>
</catalog>
```


### updated XML

```xml 
<?xml version="1.0" encoding="utf-8"?>
<catalog>
	<book id="bk101">
		<author>Stephen King</author>
		<title>XML Developer's Guide</title>
		<genre>Computer</genre>
		<price>449.5</price>
		<publish_date>2000-10-01</publish_date>
		<description>An in-depth look at creating applications 
      with XML.</description>
	</book>
	<book id="bk102">
		<author>Stephen King</author>
		<title>Midnight Rain</title>
		<genre>Fantasy</genre>
		<price>59.5</price>
		<publish_date>2000-12-16</publish_date>
		<description>A former architect battles corporate zombies, 
      an evil sorceress, and her own childhood to become queen 
      of the world.</description>
	</book>
	<book id="bk103">
		<author>Stephen King</author>
		<title>Maeve Ascendant</title>
		<genre>Fantasy</genre>
		<price>59.5</price>
		<publish_date>2000-11-17</publish_date>
		<description>After the collapse of a nanotechnology 
      society in England, the young survivors lay the 
      foundation for a new society.</description>
	</book>
	<book id="bk104">
		<author>Stephen King</author>
		<title>Oberon's Legacy</title>
		<genre>Fantasy</genre>
		<price>59.5</price>
		<publish_date>2001-03-10</publish_date>
		<description>In post-apocalypse England, the mysterious 
      agent known only as Oberon helps to create a new life 
      for the inhabitants of London. Sequel to Maeve 
      Ascendant.</description>
	</book>
	<book id="bk105">
		<author>Stephen King</author>
		<title>The Sundered Grail</title>
		<genre>Fantasy</genre>
		<price>59.5</price>
		<publish_date>2001-09-10</publish_date>
		<description>The two daughters of Maeve, half-sisters, 
      battle one another for control of England. Sequel to 
      Oberon's Legacy.</description>
	</book>
	<book id="bk106">
		<author>Stephen King</author>
		<title>Lover Birds</title>
		<genre>Romance</genre>
		<price>49.5</price>
		<publish_date>2000-09-02</publish_date>
		<description>When Carla meets Paul at an ornithology 
      conference, tempers fly as feathers get ruffled.</description>
	</book>
	<book id="bk107">
		<author>Stephen King</author>
		<title>Splish Splash</title>
		<genre>Romance</genre>
		<price>49.5</price>
		<publish_date>2000-11-02</publish_date>
		<description>A deep sea diver finds true love twenty 
      thousand leagues beneath the sea.</description>
	</book>
	<book id="bk108">
		<author>Stephen King</author>
		<title>Creepy Crawlies</title>
		<genre>Horror</genre>
		<price>49.5</price>
		<publish_date>2000-12-06</publish_date>
		<description>An anthology of horror stories about roaches,
      centipedes, scorpions  and other insects.</description>
	</book>
	<book id="bk109">
		<author>Stephen King</author>
		<title>Paradox Lost</title>
		<genre>Science Fiction</genre>
		<price>69.5</price>
		<publish_date>2000-11-02</publish_date>
		<description>After an inadvertant trip through a Heisenberg
      Uncertainty Device, James Salway discovers the problems 
      of being quantum.</description>
	</book>
	<book id="bk110">
		<author>Stephen King</author>
		<title>Microsoft .NET: The Programming Bible</title>
		<genre>Computer</genre>
		<price>369.5</price>
		<publish_date>2000-12-09</publish_date>
		<description>Microsoft's .NET initiative is explored in 
      detail in this deep programmer's reference.</description>
	</book>
	<book id="bk111">
		<author>Stephen King</author>
		<title>MSXML3: A Comprehensive Guide</title>
		<genre>Computer</genre>
		<price>369.5</price>
		<publish_date>2000-12-01</publish_date>
		<description>The Microsoft MSXML3 parser is covered in 
      detail, with attention to XML DOM interfaces, XSLT processing, 
      SAX and more.</description>
	</book>
	<book id="bk112">
		<author>Stephen King</author>
		<title>Visual Studio 7: A Comprehensive Guide</title>
		<genre>Computer</genre>
		<price>499.5</price>
		<publish_date>2001-04-16</publish_date>
		<description>Microsoft Visual Studio 7 is explored in depth,
      looking at how Visual Basic, Visual C++, C#, and ASP+ are 
      integrated into a comprehensive development 
      environment.</description>
	</book>
</catalog>
```