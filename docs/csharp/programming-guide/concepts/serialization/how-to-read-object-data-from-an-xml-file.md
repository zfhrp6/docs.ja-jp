---
title: '方法: XML ファイルからオブジェクト データを読み込む (C#)'
ms.date: 07/20/2015
ms.assetid: 6ad60d96-a4d9-48e6-a8b0-d7f6f803cafa
ms.openlocfilehash: 59110a5bd0fe738239c0ca8b177a8c775db99ccf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-read-object-data-from-an-xml-file-c"></a><span data-ttu-id="5203f-102">方法: XML ファイルからオブジェクト データを読み込む (C#)</span><span class="sxs-lookup"><span data-stu-id="5203f-102">How to: Read Object Data from an XML File (C#)</span></span>
<span data-ttu-id="5203f-103">次の例では、<xref:System.Xml.Serialization.XmlSerializer> クラスを使用して、XML ファイルに以前に書き込まれたオブジェクト データを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="5203f-103">This example reads object data that was previously written to an XML file using the <xref:System.Xml.Serialization.XmlSerializer> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5203f-104">例</span><span class="sxs-lookup"><span data-stu-id="5203f-104">Example</span></span>  
  
```csharp  
public class Book  
{  
    public String title;  
}         
  
public void ReadXML()  
{  
    // First write something so that there is something to read ...  
    var b = new Book { title = "Serialization Overview" };  
    var writer = new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    var wfile = new System.IO.StreamWriter(@"c:\temp\SerializationOverview.xml");  
    writer.Serialize(wfile, b);  
    wfile.Close();  
  
    // Now we can read the serialized book ...  
    System.Xml.Serialization.XmlSerializer reader =   
        new System.Xml.Serialization.XmlSerializer(typeof(Book));  
    System.IO.StreamReader file = new System.IO.StreamReader(  
        @"c:\temp\SerializationOverview.xml");  
    Book overview =  (Book)reader.Deserialize(file);  
    file.Close();  
  
    Console.WriteLine(overview.title);  
  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5203f-105">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="5203f-105">Compiling the Code</span></span>  
 <span data-ttu-id="5203f-106">ファイル名 "c:\temp\SerializationOverview.xml" を、シリアル化されたデータを含むファイルの名前に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="5203f-106">Replace the file name "c:\temp\SerializationOverview.xml" with the name of the file containing the serialized data.</span></span> <span data-ttu-id="5203f-107">データのシリアル化の詳細については、「[方法: XML ファイルにオブジェクト データを書き込む (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5203f-107">For more information about serializing data, see [How to: Write Object Data to an XML File (C#)](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md).</span></span>  
  
 <span data-ttu-id="5203f-108">クラスには、パラメーターのないパブリック コンストラクターが必要です。</span><span class="sxs-lookup"><span data-stu-id="5203f-108">The class must have a public constructor without parameters.</span></span>  
  
 <span data-ttu-id="5203f-109">パブリック プロパティとパブリック フィールドだけが逆シリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="5203f-109">Only public properties and fields are deserialized.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5203f-110">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="5203f-110">Robust Programming</span></span>  
 <span data-ttu-id="5203f-111">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="5203f-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="5203f-112">シリアル化されるクラスにパブリックなパラメーターなしのコンストラクターがない場合</span><span class="sxs-lookup"><span data-stu-id="5203f-112">The class being serialized does not have a public, parameterless constructor.</span></span>  
  
-   <span data-ttu-id="5203f-113">ファイル内のデータが、逆シリアル化されるクラスのデータを表していない場合。</span><span class="sxs-lookup"><span data-stu-id="5203f-113">The data in the file does not represent data from the class to be deserialized.</span></span>  
  
-   <span data-ttu-id="5203f-114">ファイルが存在しない (<xref:System.IO.IOException>)。</span><span class="sxs-lookup"><span data-stu-id="5203f-114">The file does not exist (<xref:System.IO.IOException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="5203f-115">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="5203f-115">.NET Framework Security</span></span>  
 <span data-ttu-id="5203f-116">入力を常に検証し、信頼できないソースから決してデータを逆シリアル化しないでください。</span><span class="sxs-lookup"><span data-stu-id="5203f-116">Always verify inputs, and never deserialize data from an untrusted source.</span></span> <span data-ttu-id="5203f-117">再作成されたオブジェクトは、そのオブジェクトを逆シリアル化したコードと同じアクセス許可を持つローカル コンピューターで実行されます。</span><span class="sxs-lookup"><span data-stu-id="5203f-117">The re-created object runs on a local computer with the permissions of the code that deserialized it.</span></span> <span data-ttu-id="5203f-118">アプリケーションでデータを使用する前に、入力をすべて検証してください。</span><span class="sxs-lookup"><span data-stu-id="5203f-118">Verify all inputs before using the data in your application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5203f-119">参照</span><span class="sxs-lookup"><span data-stu-id="5203f-119">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 [<span data-ttu-id="5203f-120">方法: XML ファイルにオブジェクト データを書き込む (C#)</span><span class="sxs-lookup"><span data-stu-id="5203f-120">How to: Write Object Data to an XML File (C#)</span></span>](../../../../csharp/programming-guide/concepts/serialization/how-to-write-object-data-to-an-xml-file.md)  
 [<span data-ttu-id="5203f-121">シリアル化 (C#)</span><span class="sxs-lookup"><span data-stu-id="5203f-121">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="5203f-122">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="5203f-122">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
