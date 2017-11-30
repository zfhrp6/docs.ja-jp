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
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c041d5d2830222f3fae09a39f1ea10eb08772388
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="xml-element-and-attribute-name-verification-when-creating-new-nodes"></a><span data-ttu-id="1a583-102">新しいノードの作成時における XML 要素名および属性名の検証</span><span class="sxs-lookup"><span data-stu-id="1a583-102">XML Element and Attribute Name Verification when Creating New Nodes</span></span>
<span data-ttu-id="1a583-103">XML ドキュメント オブジェクト モデル (DOM) は、新しい要素ノードまたは属性ノードを作成するときに名前の有効性を確認します。</span><span class="sxs-lookup"><span data-stu-id="1a583-103">The XML Document Object Model (DOM) checks the validity of the names when creating new element nodes or attribute nodes.</span></span> <span data-ttu-id="1a583-104">名前に無効な文字が含まれていると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="1a583-104">If the names contain illegal characters, an exception is thrown.</span></span> <span data-ttu-id="1a583-105">名前が有効であり、エンコードされた正常に使用する必要があることを確認して、 **XmlConvert**クラスを名前をエンコードおよびデコードし、アプリケーション レベルに戻ります。</span><span class="sxs-lookup"><span data-stu-id="1a583-105">To ensure that names are valid and encoded correctly, you need to use the **XmlConvert** class to encode the name and decode it back at an application level.</span></span> <span data-ttu-id="1a583-106">**XmlWriter**整形式 XML が生成されることを確認する追加の作業を行う方法があります。</span><span class="sxs-lookup"><span data-stu-id="1a583-106">The **XmlWriter** has methods that do additional work to ensure well-formed XML is generated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a583-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="1a583-107">See Also</span></span>  
 [<span data-ttu-id="1a583-108">XML ドキュメント オブジェクト モデル (DOM)</span><span class="sxs-lookup"><span data-stu-id="1a583-108">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
