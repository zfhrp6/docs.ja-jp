---
title: '方法: XML ファイルにオブジェクト データを書き込む (C#)'
ms.date: 07/20/2015
ms.assetid: 7681eb98-703d-4005-a369-26a7bca0f894
ms.openlocfilehash: 1c8bfd00452cee63456bc3bf64ccf4a0c61aa06e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-object-data-to-an-xml-file-c"></a><span data-ttu-id="6c256-102">方法: XML ファイルにオブジェクト データを書き込む (C#)</span><span class="sxs-lookup"><span data-stu-id="6c256-102">How to: Write Object Data to an XML File (C#)</span></span>
<span data-ttu-id="6c256-103"><xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、クラスから XML ファイルにオブジェクトを書き込む例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="6c256-103">This example writes the object from a class to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c256-104">例</span><span class="sxs-lookup"><span data-stu-id="6c256-104">Example</span></span>  
  
```csharp  
public class XMLWrite  
{  
  
   static void Main(string[] args)  
    {  
        WriteXML();  
    }  
  
    public class Book  
    {  
        public String title;   
    }  
  
    public static void WriteXML()  
    {  
        Book overview = new Book();  
        overview.title = "Serialization Overview";  
        System.Xml.Serialization.XmlSerializer writer =   
            new System.Xml.Serialization.XmlSerializer(typeof(Book));  
  
        var path = Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "//SerializationOverview.xml";  
        System.IO.FileStream file = System.IO.File.Create(path);  
  
        writer.Serialize(file, overview);  
        file.Close();  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6c256-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6c256-105">Compiling the Code</span></span>  
 <span data-ttu-id="6c256-106">クラスには、パラメーターのないパブリック コンストラクターが必要です。</span><span class="sxs-lookup"><span data-stu-id="6c256-106">The class must have a public constructor without parameters.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6c256-107">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="6c256-107">Robust Programming</span></span>  
 <span data-ttu-id="6c256-108">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6c256-108">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="6c256-109">シリアル化されるクラスにパブリックなパラメーターなしのコンストラクターがない場合</span><span class="sxs-lookup"><span data-stu-id="6c256-109">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="6c256-110">ファイルが存在するものの、読み取り専用の場合 (<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="6c256-110">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="6c256-111">パスが長すぎる (<xref:System.IO.PathTooLongException>)。</span><span class="sxs-lookup"><span data-stu-id="6c256-111">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="6c256-112">ディスクの空き領域がない場合 (<xref:System.IO.IOException>)</span><span class="sxs-lookup"><span data-stu-id="6c256-112">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6c256-113">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="6c256-113">.NET Framework Security</span></span>  
 <span data-ttu-id="6c256-114">次のコード例では、ファイルが存在しない場合は新規にファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="6c256-114">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="6c256-115">アプリケーションでファイルを作成する必要がある場合、そのアプリケーションにはフォルダーに対する `Create` アクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="6c256-115">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="6c256-116">ファイルが既に存在する場合、アプリケーションに必要なのは、より低い権限である `Write` アクセスだけです。</span><span class="sxs-lookup"><span data-stu-id="6c256-116">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="6c256-117">フォルダーに対して `Read` アクセスを許可するのではなく、可能な限りアプリケーションの配置時にファイルを作成しておき、1 つのファイルに対してのみ `Create` アクセスを許可する方が安全です。</span><span class="sxs-lookup"><span data-stu-id="6c256-117">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c256-118">参照</span><span class="sxs-lookup"><span data-stu-id="6c256-118">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="6c256-119">方法: XML ファイルからオブジェクト データを読み込む (C#)</span><span class="sxs-lookup"><span data-stu-id="6c256-119">How to: Read Object Data from an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-read-object-data-from-an-xml-file.md)  
 [<span data-ttu-id="6c256-120">シリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="6c256-120">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)
