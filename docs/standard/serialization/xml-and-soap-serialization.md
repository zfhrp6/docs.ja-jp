---
title: XML シリアル化および SOAP シリアル化
ms.date: 03/30/2017
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
- serialization, about serialization
- XML serialization
- serialization
ms.assetid: 832ac524-21bc-419a-a27b-ca8bfc45840f
ms.openlocfilehash: 4ca812c03949cb6a2cb903ae041e54311e9486bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="xml-and-soap-serialization"></a>XML シリアル化および SOAP シリアル化
XML シリアル化とは、オブジェクトのパブリック フィールドやパブリック プロパティ、またはメソッドのパラメーターや戻り値を、特定の XML スキーマ定義言語 (XSD: XML Schema Definition Language) ドキュメントに準拠する XML ストリームに変換 (シリアル化) する処理です。 XML シリアル化によって、パブリック プロパティおよびパブリック フィールドを含むクラスの型が厳密に指定され、それらのパブリック メンバーは格納または転送できるようにシリアル形式 (この場合は XML) に変換されます。  
  
 XML はオープン標準であるため、XML ストリームは、プラットフォームに関係なく、必要に応じて任意のアプリケーションで処理できます。 たとえば、ASP.NET を使用して作成された XML Web サービスは、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、インターネット全体またはイントラネット上の XML Web サービス アプリケーション間でデータを受け渡しする XML ストリームを作成します。 一方、逆シリアル化は、このような XML ストリームからデータを取得して、元のオブジェクトを再構築します。  
  
 XML シリアル化を使用して、SOAP 仕様に準拠する XML ストリームにオブジェクトをシリアル化することもできます。 SOAP は、XML を使用してプロシージャ呼び出しを転送するために特別にデザインされた、XML に基づくプロトコルです。  
  
 オブジェクトをシリアル化または逆シリアル化するには、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用します。 また、シリアル化する対象のクラスを作成するには、XML スキーマ定義ツールを使用します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML シリアル化の概要](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 シリアル化、特に XML シリアル化の一般的な定義を示します。  
  
 [方法 : オブジェクトをシリアル化する](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 オブジェクトをシリアル化するための詳細な手順について説明します。  
  
 [方法 : オブジェクトを逆シリアル化する](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
 オブジェクトを逆シリアル化するための詳細な手順について説明します。  
  
 [XML シリアル化の例](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 XML シリアル化の基本事項を示す例を紹介します。  
  
 [XML スキーマ定義ツールと XML シリアル化](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 XML スキーマ定義ツールを使用して、特定の XML スキーマ定義言語 (XSD) スキーマに準拠するクラスを作成したり、.dll ファイルから XML スキーマを生成したりする方法について説明します。  
  
 [属性を使用した XML シリアル化の制御](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 属性を使用してシリアル化を制御する方法について説明します。  
  
 [XML シリアル化を制御する属性](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 XML シリアル化の制御に使用する属性を示します。  
  
 [方法 : XML ストリームの代替要素名を指定する](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 シリアル化のオーバーライドにより、複数の XML ストリームを生成する方法を示す高度なシナリオを紹介します。  
  
 [方法 : 派生クラスのシリアル化を制御する](../../../docs/standard/serialization/how-to-control-serialization-of-derived-classes.md)  
 派生クラスのシリアル化の制御方法を示す例を紹介します。  
  
 [方法 : XML 要素および XML 属性名を修飾する](../../../docs/standard/serialization/how-to-qualify-xml-element-and-xml-attribute-names.md)  
 XML ストリームでの XML 名前空間の使用方法を定義および制御する方法について説明します。  
  
 [XML Web サービスを使用した XML シリアル化](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
 XML Web サービスでの XML シリアル化の使用方法について説明します。  
  
 [方法 : オブジェクトを SOAP エンコード済み XML ストリームとしてシリアル化する](../../../docs/standard/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)  
 <xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、W3C (World Wide Web Consortium) (www.w3.org) のドキュメント『Simple Object Access Protocol (SOAP) 1.1』のセクション 5 に準拠する、エンコード済みの SOAP XML ストリームを作成する方法について説明します。  
  
 [方法 : SOAP エンコード済み XML シリアル化をオーバーライドする](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)  
 SOAP メッセージとしてのオブジェクトの XML シリアル化をオーバーライドするプロセスについて説明します。  
  
 [エンコード済み SOAP シリアル化を制御する属性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 SOAP エンコード済みのシリアル化の制御に使用する属性を示します。  
  
 [\<system.xml.serialization> 要素](../../../docs/standard/serialization/system-xml-serialization-element.md)  
 XML シリアル化を制御する最上位の構成要素です。  
  
 [\<dateTimeSerialization> 要素](../../../docs/standard/serialization/datetimeserialization-element.md)  
 <xref:System.DateTime> オブジェクトのシリアル化モードを制御します。  
  
 [\<schemaImporterExtensions> 要素](../../../docs/standard/serialization/schemaimporterextensions-element.md)  
 <xref:System.Xml.Serialization.XmlSchemaImporter> クラスによって使用される型を含みます。  
  
 [\<xmlSchemaImporterExtensions> の \<add> 要素](../../../docs/standard/serialization/add-element-for-xmlschemaimporterextensions.md)  
 <xref:System.Xml.Serialization.XmlSchemaImporter> クラスによって使用される型を追加します。  
  
## <a name="related-sections"></a>関連項目  
 [高度な開発テクノロジ](https://msdn.microsoft.com/library/c4a7e341-f0c6-4df4-a74f-223387ac6e4e)  
 .NET Framework での高度な開発タスクと技法に関する詳細情報へのリンクを示します。  
  
 [ASP.NET と XML Web サービス クライアントを使用して作成した XML Web サービス](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)  
 ASP.NET を使用した XML Web サービスのプログラミング方法について説明するトピックを示します。  
  
## <a name="see-also"></a>関連項目  
 [バイナリ シリアル化](../../../docs/standard/serialization/binary-serialization.md)
