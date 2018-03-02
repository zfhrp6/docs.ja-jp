---
title: "新しいノードの作成時における XML 要素名および属性名の検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b489f647-a175-4659-ada4-170058bb41d0
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 36b9761cefb1dba47c88d053773c89e4312dee9d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="b4fe1-102">新しいノードの作成時における XML 要素名および属性名の検証</span><span class="sxs-lookup"><span data-stu-id="b4fe1-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="b4fe1-103">XML ドキュメント オブジェクト モデル (DOM) は、新しい要素ノードまたは属性ノードを作成するときに名前の有効性を確認します。</span><span class="sxs-lookup"><span data-stu-id="b4fe1-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="b4fe1-104">名前に無効な文字が含まれていると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="b4fe1-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="b4fe1-105">名前が正しくエンコードされ、有効であることを保証するには、**XmlConvert** クラスを使用して名前をエンコードし、アプリケーション レベルで名前をデコードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4fe1-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="b4fe1-106">**XmlWriter** には、整形式の XML を生成するための追加の処理を行うメソッドが用意されています。</span><span class="sxs-lookup"><span data-stu-id="b4fe1-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4fe1-107">参照</span><span class="sxs-lookup"><span data-stu-id="b4fe1-107">See Also</span></span>  
 [<span data-ttu-id="b4fe1-108">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="b4fe1-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
