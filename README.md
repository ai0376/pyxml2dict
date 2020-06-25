
pyxml2dict
===============

pyxml2dict is an open source python library, which used for converting xml to python dict

pyxml2dict is licensed under the GPL-3.0

Prefix the attribute in the dictionary @attribute , the value corresponding to key is #text


Installing
===============
Install with pip:

```

    $pip install pyxml2dict
```
Usage
===============

```

  from pyxml2dict import XML2Dict

  if __name__ == '__main__':
      xml_str1 = """<root id="1"><items><item>1</item><item>2</item></items></root>"""
      xml_str2 = """<root id="1"><age>20</age><items><item id="0">1</item><item>2</item></items></root>"""
      xml2dict = XML2Dict()
      print xml2dict.fromstring(xml_str1)
      print xml2dict.fromstring(xml_str2)
      #if you want namespace to be removed then:
      xml_str3 = """<root id="1" xmlns="somenamespace"><items><item>1</item><item>2</item></items></root>"""
      print xml2dict.fromstring(xml_str3)
      print xml2dict.fromstring(xml_str3, remove_namespace=True)
```
	  
**print result**

```

 {'root': {'items': {'item': ['1', '2']}, '@id': '1'}}

 {'root': {'items': {'item': [{'#text': '1', '@id': '0'}, '2']}, 'age': '20', '@id': '1'}}

 {'{somenamespace}root': {'@id': '1', '{somenamespace}items': {'{somenamespace}item': ['1', '2']}}}
 
 {'root': {'items': {'item': ['1', '2']}, '@id': '1'}}
 ```

Thanks
===============

In XML2Dict , *_parse_node* algorithm comes from https://github.com/undefine1995/xml2dict,  It's very useful. Thanks for undefine1994.