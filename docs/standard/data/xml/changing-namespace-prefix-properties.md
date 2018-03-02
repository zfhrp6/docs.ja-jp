---
title: "名前空間プレフィックス プロパティの変更"
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
ms.assetid: d5c87cbe-4d69-429f-aad5-3103c2ca2770
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3cb0db0fbffa5f42fb09f29da2976727451e3741
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="changing-namespace-prefix-properties"></a><span data-ttu-id="38e79-102">名前空間プレフィックス プロパティの変更</span><span class="sxs-lookup"><span data-stu-id="38e79-102">Changing Namespace Prefix Properties</span></span>
<span data-ttu-id="38e79-103">**XmlNode** クラスを使用すると、特定のノードに関連付けられた名前空間プレフィックスを変更できます。</span><span class="sxs-lookup"><span data-stu-id="38e79-103">The **XmlNode** class allows you to change the namespace prefix associated with a given node.</span></span> <span data-ttu-id="38e79-104">たとえば、要素のプレフィックスを変更するコードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="38e79-104">For example, the following code shows the prefix of an element being changed.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "b"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<a:test xmlns:a='123' xmlns:b='456'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "b";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="38e79-105">**出力**</span><span class="sxs-lookup"><span data-stu-id="38e79-105">**Output**</span></span>  
  
```xml  
<b:test xmlns:a="123" xmlns:b="456" />  
```  
  
 <span data-ttu-id="38e79-106">ノードのプレフィックスを変更しても、名前空間は変更されません。</span><span class="sxs-lookup"><span data-stu-id="38e79-106">Changing the prefix of a node does not change its namespace.</span></span> <span data-ttu-id="38e79-107">名前空間を設定できるのは、ノードを作成するときだけです。</span><span class="sxs-lookup"><span data-stu-id="38e79-107">The namespace can only be set when the node is created.</span></span> <span data-ttu-id="38e79-108">ツリーを永続化するときには、設定したプレフィックスに適合するように新しい名前空間の属性も永続化されます。</span><span class="sxs-lookup"><span data-stu-id="38e79-108">When you persist the tree, new namespace attributes may be persisted out to satisfy the prefix you set.</span></span> <span data-ttu-id="38e79-109">新しい名前空間を作成できない場合は、プレフィックスが変更され、ノードにはそのローカル名と名前空間が保持されます。</span><span class="sxs-lookup"><span data-stu-id="38e79-109">If the new namespace cannot be created, then the prefix is changed so the node preserves its local name and namespace.</span></span> <span data-ttu-id="38e79-110">名前空間の属性を追加する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="38e79-110">The following example shows a namespace attribute being added.</span></span>  
  
```vb  
Dim doc as XmlDocument = new XmlDocument()  
doc.LoadXml("<test xmlns='123'/>")  
Dim e as XmlElement = doc.DocumentElement  
e.Prefix = "a"  
Console.WriteLine(doc.InnerXml)  
```  
  
```csharp  
XmlDocument doc = new XmlDocument();  
doc.LoadXml("<test xmlns='123'/>");  
XmlElement e = doc.DocumentElement;         
e.Prefix = "a";  
Console.WriteLine(doc.InnerXml);  
```  
  
 <span data-ttu-id="38e79-111">**出力**</span><span class="sxs-lookup"><span data-stu-id="38e79-111">**Output**</span></span>  
  
```xml  
<a:test xmlns="123" xmlns:a="123" />  
```  
  
 <span data-ttu-id="38e79-112">**doc.InnerXml** の呼び出しの結果としてツリーが文字列に永続化されるとき、`test` 要素の名前空間を保持するために `xmlns:a='123'` という属性が追加されます。</span><span class="sxs-lookup"><span data-stu-id="38e79-112">When the tree was persisted to a string as a result of the call to **doc.InnerXml**, the `xmlns:a='123'` attribute was added to preserve the namespace of the `test` element.</span></span> <span data-ttu-id="38e79-113">`'123'` の元の値は `'123'` だったので、そのまま  として残ります。</span><span class="sxs-lookup"><span data-stu-id="38e79-113">It was `'123'`, and it remained `'123'`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38e79-114">参照</span><span class="sxs-lookup"><span data-stu-id="38e79-114">See Also</span></span>  
 [<span data-ttu-id="38e79-115">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="38e79-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
