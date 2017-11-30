---
title: "方法: XML ファイル (Visual Basic) からオブジェクト データを読み込む"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e1423bf-74a4-4dde-a3bb-ae1bfc0a68ed
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 47e5c614f2083ec2c595bba9c9454ecc5f61c786
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a>方法: XML ファイル (Visual Basic) からオブジェクト データを読み込む
次の例では、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、XML ファイルに以前に書き込まれたオブジェクト データを読み込みます。  
  
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
 ファイル名 "c:\temp\SerializationOverview.xml" を、シリアル化されたデータを含むファイルの名前に置き換えます。 データのシリアル化に関する詳細については、次を参照してください。[する方法: XML ファイル (Visual Basic) にオブジェクト データを書き込む](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)です。  
  
 クラスには、パラメーターのないパブリック コンストラクターが必要です。  
  
 パブリック プロパティとパブリック フィールドだけが逆シリアル化されます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   シリアル化されるクラスにパブリックなパラメーターなしのコンストラクターがない場合  
  
-   ファイル内のデータが、逆シリアル化されるクラスのデータを表していない場合。  
  
-   ファイルが存在しない (<xref:System.IO.IOException>)。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 入力を常に検証し、信頼できないソースから決してデータを逆シリアル化しないでください。 再作成されたオブジェクトは、そのオブジェクトを逆シリアル化したコードと同じアクセス許可を持つローカル コンピューターで実行されます。 アプリケーションでデータを使用する前に、入力をすべて検証してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.StreamWriter>  
 [方法: XML ファイルにオブジェクト データを書き込む (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [シリアル化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [Visual Basic プログラミング ガイド](../../../../visual-basic/programming-guide/index.md)
