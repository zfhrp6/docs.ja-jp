---
title: "方法: XML ファイル (Visual Basic の場合) からオブジェクト データを読み込む |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c448d79a88517925712f79ed061aa90933e3f6d1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>方法: XML ファイル (Visual Basic の場合) からオブジェクト データを読み込む
この例の<xref:System.Xml.Serialization.XmlSerializer>クラス</xref:System.Xml.Serialization.XmlSerializer>を使用して XML ファイルに書き込まれた以前オブジェクト データを読み取ります  
  
## <a name="example"></a>例  
  
```vb  
Public Class Book  
    Public Title As String  
End Class  
  
Public Sub ReadXML()  
    Dim reader As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
    Dim file As New System.IO.StreamReader(  
        "c:\temp\SerializationOverview.xml")  
    Dim overview As Book  
    overview = CType(reader.Deserialize(file), Book)  
    Console.WriteLine(overview.Title)  
End Sub  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 ファイル名"c:\temp\SerializationOverview.xml"をシリアル化されたデータを含むファイルの名前に置き換えます。 データのシリアル化に関する詳細については、次を参照してください。[方法: XML ファイル (Visual Basic) にオブジェクト データを書き込む](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)します。  
  
 クラスには、パラメーターのないパブリック コンストラクターが必要です。  
  
 パブリック プロパティおよびフィールドだけを逆シリアル化します。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   シリアル化されるクラスにパブリックなパラメーターなしのコンストラクターがない場合  
  
-   ファイル内のデータは、逆シリアル化するクラスからデータを表していません。  
  
-   ファイルが存在しない (<xref:System.IO.IOException>).</xref:System.IO.IOException>  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 常に、入力を確認し、決して、信頼できないソースからデータを逆シリアル化します。 再作成されたオブジェクトは、逆シリアル化したコードのアクセス許可を持つローカル コンピューターで実行されます。 アプリケーションでデータを使用する前に、入力をすべて検証してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.StreamWriter></xref:System.IO.StreamWriter>   
 [方法: XML ファイル (Visual Basic) にオブジェクト データを書き込む](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)   
 [シリアル化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)   
 [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md)
