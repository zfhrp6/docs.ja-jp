---
title: "XmlSchemaCollection を使用した XDR 検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 00833027-1428-4586-83c1-42f5de3323d1
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fab67e10aa0562b59f8c7704a5ca1feeb66d6208
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="xdr-validation-with-xmlschemacollection"></a>XmlSchemaCollection を使用した XDR 検証
に対して検証するときは、Xml-data Reduced (XDR) スキーマが格納されている場合、 **XmlSchemaCollection**URI では、スキーマがコレクションに追加したときに指定された名前空間に関連付けられています。 **XmlValidatingReader** XML ドキュメント内の名前空間 URI をコレクション内の URI に対応するスキーマにマップします。  
  
> [!IMPORTANT]
>  <xref:System.Xml.Schema.XmlSchemaCollection> クラスは廃止されており、<xref:System.Xml.Schema.XmlSchemaSet> クラスに置き換えられています。 詳細については、<xref:System.Xml.Schema.XmlSchemaSet>クラス」を参照して[スキーマのコンパイルのための XmlSchemaSet](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)です。  
  
 たとえば、XML ドキュメントのルート要素が`<bookstore xmlns="urn:newbooks-schema">`にスキーマを追加すると、 **XmlSchemaCollection**次のように、同じ名前空間を参照しています。  
  
```  
xsc.Add("urn:newbooks-schema", "newbooks.xdr")  
```  
  
 次のコード例を作成、 **XmlValidatingReader**を受け取る、 **XmlTextReader** XDR スキーマ HeadCount.xdr に追加し、 **XmlSchemaCollection**です。  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
Imports System.Xml.Schema  
  
Namespace ValidationSample  
  
   Class Sample  
  
      Public Shared Sub Main()  
         Dim tr As New XmlTextReader("HeadCount.xml")  
         Dim vr As New XmlValidatingReader(tr)  
  
         vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr")  
         vr.ValidationType = ValidationType.XDR  
         AddHandler vr.ValidationEventHandler, AddressOf ValidationHandler  
  
         While vr.Read()  
            PrintTypeInfo(vr)  
            If vr.NodeType = XmlNodeType.Element Then  
               While vr.MoveToNextAttribute()  
                  PrintTypeInfo(vr)  
               End While  
            End If  
         End While  
         Console.WriteLine("Validation finished")  
      End Sub  
      ' Main  
  
      Public Shared Sub PrintTypeInfo(vr As XmlValidatingReader)  
         If Not (vr.SchemaType Is Nothing) Then  
            If TypeOf vr.SchemaType Is XmlSchemaDatatype Or TypeOf vr.SchemaType Is XmlSchemaSimpleType Then  
               Dim value As Object = vr.ReadTypedValue()  
               Console.WriteLine("{0}({1},{2}):{3}", vr.NodeType, vr.Name, value.GetType().Name, value)  
            End If  
         End If  
      End Sub  
      ' PrintTypeInfo  
  
      Public Shared Sub ValidationHandler(sender As Object, args As ValidationEventArgs)  
         Console.WriteLine("***Validation error")  
         Console.WriteLine("Severity:{0}", args.Severity)  
         Console.WriteLine("Message:{0}", args.Message)  
      End Sub  
      ' ValidationHandler  
   End Class  
   ' Sample  
End Namespace  
' ValidationSample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
using System.Xml.Schema;  
  
namespace ValidationSample  
{  
   class Sample  
   {  
      public static void Main()  
      {  
         XmlTextReader tr = new XmlTextReader("HeadCount.xml");  
         XmlValidatingReader vr = new XmlValidatingReader(tr);  
  
         vr.Schemas.Add("xdrHeadCount", "HeadCount.xdr");  
         vr.ValidationType = ValidationType.XDR;  
         vr.ValidationEventHandler += new ValidationEventHandler (ValidationHandler);  
  
         while(vr.Read())  
         {  
            PrintTypeInfo(vr);  
            if(vr.NodeType == XmlNodeType.Element)  
            {  
               while(vr.MoveToNextAttribute())  
                  PrintTypeInfo(vr);  
            }  
         }  
         Console.WriteLine("Validation finished");  
      }  
  
      public static void PrintTypeInfo(XmlValidatingReader vr)  
      {  
         if(vr.SchemaType != null)  
         {  
            if(vr.SchemaType is XmlSchemaDatatype || vr.SchemaType is XmlSchemaSimpleType)  
            {  
               object value = vr.ReadTypedValue();  
               Console.WriteLine("{0}({1},{2}):{3}", vr.NodeType, vr.Name, value.GetType().Name, value);  
            }  
         }  
      }  
  
      public static void ValidationHandler(object sender, ValidationEventArgs args)  
      {  
         Console.WriteLine("***Validation error");  
         Console.WriteLine("\tSeverity:{0}", args.Severity);  
         Console.WriteLine("\tMessage:{0}", args.Message);  
      }  
   }  
}  
```  
  
 検証対象の入力ファイル HeadCount.xml の内容について、次に概略を示します。  
  
```xml  
<!--Load HeadCount.xdr in SchemaCollection for Validation-->  
<HeadCount xmlns='xdrHeadCount'>  
   <Name>Waldo Pepper</Name>  
   <Name>Red Pepper</Name>  
</HeadCount>  
```  
  
 検証の基準とする XDR スキーマ ファイル HeadCount.xdr の内容について、次に概略を示します。  
  
```xml  
<Schema xmlns="urn:schemas-microsoft-com:xml-data" xmlns:dt="urn:schemas-microsoft-com:datatypes">  
   <ElementType name="Name" content="textOnly"/>  
   <AttributeType name="Bldg" default="2"/>  
   <ElementType name="HeadCount" content="eltOnly">  
      <element type="Name"/>  
      <attribute type="Bldg"/>  
   </ElementType>  
</Schema>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Xml.XmlValidatingReader.ValidationType%2A>  
 <!--zz <xref:System.Xml.XmlValidatingReader.Settings%2A>-->  `System.Xml.XmlValidatingReader.Settings`  
 [XmlSchemaCollection スキーマのコンパイル](../../../../docs/standard/data/xml/xmlschemacollection-schema-compilation.md)
