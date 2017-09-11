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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 3b9697f763a2d781c37960d46cbc7fa4536c84b4
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-read-object-data-from-an-xml-file-visual-basic"></a><span data-ttu-id="01569-102">方法: XML ファイル (Visual Basic の場合) からオブジェクト データを読み込む</span><span class="sxs-lookup"><span data-stu-id="01569-102">How to: Read Object Data from an XML File (Visual Basic)</span></span>
<span data-ttu-id="01569-103">この例の<xref:System.Xml.Serialization.XmlSerializer>クラス</xref:System.Xml.Serialization.XmlSerializer>を使用して XML ファイルに書き込まれた以前オブジェクト データを読み取ります</span><span class="sxs-lookup"><span data-stu-id="01569-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01569-104">例</span><span class="sxs-lookup"><span data-stu-id="01569-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="01569-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="01569-105">Compiling the Code</span></span>  
 <span data-ttu-id="01569-106">ファイル名"c:\temp\SerializationOverview.xml"をシリアル化されたデータを含むファイルの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="01569-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="01569-107">データのシリアル化に関する詳細については、次を参照してください。[方法: XML ファイル (Visual Basic) にオブジェクト データを書き込む](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)します。</span><span class="sxs-lookup"><span data-stu-id="01569-107">For more information about serializing data, see [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="01569-108">クラスには、パラメーターのないパブリック コンストラクターが必要です。</span><span class="sxs-lookup"><span data-stu-id="01569-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="01569-109">パブリック プロパティおよびフィールドだけを逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="01569-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="01569-110">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="01569-110">Robust Programming</span></span>  
 <span data-ttu-id="01569-111">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="01569-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="01569-112">シリアル化されるクラスにパブリックなパラメーターなしのコンストラクターがない場合</span><span class="sxs-lookup"><span data-stu-id="01569-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="01569-113">ファイル内のデータは、逆シリアル化するクラスからデータを表していません。</span><span class="sxs-lookup"><span data-stu-id="01569-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="01569-114">ファイルが存在しない (<xref:System.IO.IOException>).</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="01569-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="01569-115">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="01569-115">.NET Framework Security</span></span>  
 <span data-ttu-id="01569-116">常に、入力を確認し、決して、信頼できないソースからデータを逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="01569-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="01569-117">再作成されたオブジェクトは、逆シリアル化したコードのアクセス許可を持つローカル コンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="01569-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="01569-118">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="01569-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01569-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="01569-119">See Also</span></span>  
 <span data-ttu-id="01569-120"><xref:System.IO.StreamWriter></xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="01569-120"><xref:System.IO.StreamWriter></span></span>   
<span data-ttu-id="01569-121"> [方法: XML ファイル (Visual Basic) にオブジェクト データを書き込む](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) </span><span class="sxs-lookup"><span data-stu-id="01569-121"> [How to: Write Object Data to an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md) </span></span>  
<span data-ttu-id="01569-122"> [シリアル化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md) </span><span class="sxs-lookup"><span data-stu-id="01569-122"> [Serialization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md) </span></span>  
<span data-ttu-id="01569-123"> [Visual Basic のプログラミング ガイド](../../../../visual-basic/programming-guide/index.md)</span><span class="sxs-lookup"><span data-stu-id="01569-123"> [Visual Basic Programming Guide](../../../../visual-basic/programming-guide/index.md)</span></span>
