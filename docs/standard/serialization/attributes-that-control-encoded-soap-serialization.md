---
title: "エンコード済み SOAP シリアル化を制御する属性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- XML serialization, attributes
- attributes [.NET Framework], XML serialization
- serialization, attributes
ms.assetid: 93ee258c-9c0f-4a08-897c-c10db7a00f91
caps.latest.revision: 8
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: a6af8cd2560bb9c39657d8e5b088954996ba2a04
ms.contentlocale: ja-jp
ms.lasthandoff: 08/21/2017

---
# <a name="attributes-that-control-encoded-soap-serialization"></a>エンコード済み SOAP シリアル化を制御する属性 
World Wide Web コンソーシアム (www.w3.org) のドキュメント『Simple Object Access Protocol (SOAP) 1.1』には、SOAP パラメーターのエンコード方法について説明したオプションのセクション (セクション 5) が含まれています。 このセクション 5 の仕様に準拠するには、<xref:System.Xml.Serialization> 名前空間で指定されている特殊な属性セットを使用する必要があります。 これらの属性をクラスやクラスのメンバーに適宜適用し、<xref:System.Xml.Serialization.XmlSerializer> を使用して、クラスのインスタンスをシリアル化します。  
  
 これらの属性、およびその適用対象と機能を次の表に示します。 これらの属性を使用する XML シリアル化の制御の詳細については、「[How to: Serialize an Object as a SOAP-Encoded XML Stream](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)」(方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する) および「[How to: Override Encoded SOAP XML Serialization](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)」(方法 : SOAP エンコード済み XML シリアル化をオーバーライドする) を参照してください。  
  
 属性の詳細については、「[属性](../../../docs/standard/attributes/index.md)」を参照してください。  
  
|属性|対象|指定内容|  
|---------------|----------------|---------------|  
|<xref:System.Xml.Serialization.SoapAttributeAttribute>|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|クラス メンバーを XML 属性としてシリアル化します。|  
|<xref:System.Xml.Serialization.SoapElementAttribute>|パブリック フィールド、パブリック プロパティ、パブリック パラメーター、または戻り値|クラスを XML 要素としてシリアル化します。|  
|<xref:System.Xml.Serialization.SoapEnumAttribute>|列挙体識別子であるパブリック フィールド|列挙体のメンバーの要素名を指定します。|  
|<xref:System.Xml.Serialization.SoapIgnoreAttribute>|パブリック プロパティとパブリック フィールド|クラスのシリアル化時に、そのクラスに含まれているプロパティまたはフィールドを無視します。|  
|<xref:System.Xml.Serialization.SoapIncludeAttribute>|パブリック派生クラス宣言、およびパブリック メソッド (Web サービス記述言語 (WSDL: Web Service Description Language) ドキュメント用)|シリアル化時に認識されるように、スキーマの生成時にその型を対象に含めます。|  
|<xref:System.Xml.Serialization.SoapTypeAttribute>|パブリック クラス宣言|クラスを XML 型としてシリアル化します。|  
  
## <a name="see-also"></a>関連項目  
 [XML シリアル化および SOAP シリアル化](../../../docs/standard/serialization/xml-and-soap-serialization.md)   
 [方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)   
 [方法 : SOAP エンコード済み XML シリアル化をオーバーライドする](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)   
 [属性](../../../docs/standard/attributes/index.md)   
 <xref:System.Xml.Serialization.XmlSerializer>   
 [方法 : オブジェクトをシリアル化する](../../../docs/standard/serialization/how-to-serialize-an-object.md)   
 [方法 : オブジェクトを逆シリアル化する](../../../docs/standard/serialization/how-to-deserialize-an-object.md)

