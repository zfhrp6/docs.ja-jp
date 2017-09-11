---
title: "方法: XML ファイル (Visual Basic) にオブジェクト データを書き込む |Microsoft ドキュメント"
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
ms.assetid: f7966480-5ed2-43ac-9894-33427436de2a
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
ms.openlocfilehash: 27131f357c1f5afc75645bff88ae5d7cd2395617
ms.contentlocale: ja-jp
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-write-object-data-to-an-xml-file-visual-basic"></a><span data-ttu-id="9757e-102">方法: XML ファイル (Visual Basic) にオブジェクト データを書き込む</span><span class="sxs-lookup"><span data-stu-id="9757e-102">How to: Write Object Data to an XML File (Visual Basic)</span></span>
<span data-ttu-id="9757e-103">この例は、オブジェクトをクラスから<xref:System.Xml.Serialization.XmlSerializer>クラス</xref:System.Xml.Serialization.XmlSerializer>を使用して XML ファイルに書き込む</span><span class="sxs-lookup"><span data-stu-id="9757e-103">TThis example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9757e-104">例</span><span class="sxs-lookup"><span data-stu-id="9757e-104">Example</span></span>  
  
```vb  
Public Module XMLWrite  
  
    Sub Main()  
        WriteXML()  
    End Sub  
  
    Public Class Book  
        Public Title As String  
    End Class  
  
    Public Sub WriteXML()  
        Dim overview As New Book  
        overview.Title = "Serialization Overview"  
        Dim writer As New System.Xml.Serialization.XmlSerializer(GetType(Book))  
        Dim file As New System.IO.StreamWriter(  
            "c:\temp\SerializationOverview.xml")  
        writer.Serialize(file, overview)  
        file.Close()  
    End Sub  
End Module  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9757e-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="9757e-105">Compiling the Code</span></span>  
 <span data-ttu-id="9757e-106">クラスには、パラメーターのないパブリック コンストラクターが必要です。</span><span class="sxs-lookup"><span data-stu-id="9757e-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9757e-107">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="9757e-107">Robust Programming</span></span>  
 <span data-ttu-id="9757e-108">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="9757e-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="9757e-109">シリアル化されるクラスにパブリックなパラメーターなしのコンストラクターがない場合</span><span class="sxs-lookup"><span data-stu-id="9757e-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="9757e-110">ファイルが存在し、読み取り専用 (<xref:System.IO.IOException>).</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="9757e-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="9757e-111">パスが長すぎます (<xref:System.IO.PathTooLongException>).</xref:System.IO.PathTooLongException></span><span class="sxs-lookup"><span data-stu-id="9757e-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="9757e-112">ディスクがいっぱい (<xref:System.IO.IOException>).</xref:System.IO.IOException></span><span class="sxs-lookup"><span data-stu-id="9757e-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="9757e-113">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="9757e-113">.NET Framework Security</span></span>  
 <span data-ttu-id="9757e-114">次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="9757e-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="9757e-115">アプリケーションでファイルを作成する必要がある場合、そのアプリケーションにはフォルダーに対する `Create` アクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="9757e-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="9757e-116">ファイルが既に存在する場合、アプリケーションに必要なのは、より低い権限である `Write` アクセスだけです。</span><span class="sxs-lookup"><span data-stu-id="9757e-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="9757e-117">フォルダーに対して `Read` アクセスを許可するのではなく、可能な限りアプリケーションの配置時にファイルを作成しておき、1 つのファイルに対してのみ `Create` アクセスを許可する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="9757e-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9757e-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="9757e-118">See Also</span></span>  
 <span data-ttu-id="9757e-119"><xref:System.IO.StreamWriter></xref:System.IO.StreamWriter></span><span class="sxs-lookup"><span data-stu-id="9757e-119"><xref:System.IO.StreamWriter></span></span>   
<span data-ttu-id="9757e-120"> [方法: XML ファイル (Visual Basic の場合) からオブジェクト データを読み込む](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md) </span><span class="sxs-lookup"><span data-stu-id="9757e-120"> [How to: Read Object Data from an XML File (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md) </span></span>  
<span data-ttu-id="9757e-121"> [シリアル化 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)</span><span class="sxs-lookup"><span data-stu-id="9757e-121"> [Serialization (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)</span></span>
