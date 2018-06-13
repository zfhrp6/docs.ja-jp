---
title: JSON シリアル化
ms.date: 03/30/2017
ms.assetid: 3c2c4747-7510-4bdf-b4fe-64f98428ef4a
ms.openlocfilehash: 389bdc8b064bda9870b33a2e4c46fdf90bb7f3ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33502511"
---
# <a name="json-serialization"></a><span data-ttu-id="4f1b5-102">JSON シリアル化</span><span class="sxs-lookup"><span data-stu-id="4f1b5-102">JSON Serialization</span></span>
<span data-ttu-id="4f1b5-103">このサンプルでは、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を使用して、JavaScript Object Notation (JSON) 形式のデータをシリアル化および逆シリアル化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-103">This sample demonstrates how to use the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> to serialize and deserialize data in the JavaScript Object Notation (JSON) format.</span></span> <span data-ttu-id="4f1b5-104">このシリアル化エンジンによって、JSON データを [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 型のインスタンスに変換したり JSON データに戻したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-104">This serialization engine converts JSON data into instances of [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types and back into JSON data.</span></span> <span data-ttu-id="4f1b5-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> では、<xref:System.Runtime.Serialization.DataContractSerializer> と同じ型をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-105"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> supports the same types as <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span> <span data-ttu-id="4f1b5-106">JSON データ形式は、特に Asynchronous JavaScript and XML (AJAX) スタイルの Web アプリケーションを作成するときに便利です。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-106">The JSON data format is especially useful when writing Asynchronous JavaScript and XML (AJAX)-style Web applications.</span></span> <span data-ttu-id="4f1b5-107">Windows Communication Foundation (WCF) での AJAX サポートは、ScriptManager コントロールを介して ASP.NET AJAX と共に使用に適しています。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-107">AJAX support in Windows Communication Foundation (WCF) is optimized for use with ASP.NET AJAX through the ScriptManager control.</span></span> <span data-ttu-id="4f1b5-108">ASP.NET AJAX を使用した Windows Communication Foundation (WCF) を使用する方法の例については、次を参照してください。、 [AJAX サンプル](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)です。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-108">For examples of how to use Windows Communication Foundation (WCF) with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f1b5-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4f1b5-110">このサンプルでは、シリアル化および逆シリアル化を示すために、`Person` データ コントラクトを使用しています。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-110">The sample uses a `Person` data contract to demonstrate serialization and deserialization.</span></span>  

```csharp
[DataContract]
class Person
{
    [DataMember]
    internal string name;

    [DataMember]
    internal int age;
}
```

 <span data-ttu-id="4f1b5-111">`Person` 型のインスタンスを JSON にシリアル化するには、最初に <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> を作成し、次に `WriteObject` メソッドを使用して JSON データをストリームに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-111">To serialize an instance of the `Person` type to JSON, create the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> first and use the `WriteObject` method to write JSON data to a stream.</span></span>  

```csharp
Person p = new Person();
//Set up Person object...
MemoryStream stream1 = new MemoryStream();
DataContractJsonSerializer ser = new DataContractJsonSerializer(typeof(Person));
ser.WriteObject(stream1, p);
```

 <span data-ttu-id="4f1b5-112">メモリ ストリームには有効な JSON データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-112">The memory stream contains valid JSON data.</span></span>
  
```json  
{"age":42,"name":"John"}  
```  
  
 <span data-ttu-id="4f1b5-113">このサンプルでは、JSON データからオブジェクトへの逆シリアル化を示します。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-113">The sample demonstrates deserializing from JSON data into an object.</span></span> <span data-ttu-id="4f1b5-114">次に、ストリームを巻き戻し、`ReadObject` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-114">You then rewind the stream and call `ReadObject`.</span></span>  

```csharp
Person p2 = (Person)ser.ReadObject(stream1);
```

 <span data-ttu-id="4f1b5-115">`p2` オブジェクトを調べることで、JSON データが正しく逆シリアル化されていることがわかります。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-115">Examining the `p2` object reveals that the JSON data has been deserialized correctly.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4f1b5-116">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-116">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4f1b5-117">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-117">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4f1b5-118">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-118">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4f1b5-119">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-119">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\JsonSerialization`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4f1b5-120">サンプルを設定、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="4f1b5-120">To set up, build and run the sample</span></span>  
  
1.  <span data-ttu-id="4f1b5-121">ソリューションをビルドします JsonSerialization.sln」の説明に従って[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-121">Build the solution JsonSerialization.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2.  <span data-ttu-id="4f1b5-122">作成されたコンソール アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="4f1b5-122">Run the resulting console application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f1b5-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f1b5-123">See Also</span></span>
