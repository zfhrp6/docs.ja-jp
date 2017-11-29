---
title: "状態データの保護"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], state data
- code security, state data
- secure coding, state data
- state data security
ms.assetid: 12671309-2877-43fe-a3df-6863507e712d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: bd41f5174f426e723ea7e069eaee8f2d367625a1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="securing-state-data"></a><span data-ttu-id="c74ff-102">状態データの保護</span><span class="sxs-lookup"><span data-stu-id="c74ff-102">Securing State Data</span></span>
<span data-ttu-id="c74ff-103">機密データの処理または任意の種類のセキュリティ決定を行うアプリケーションは、そのデータを自らの制御下に置き、潜在的に悪意がある他のコードがそのデータに直接アクセスできないようにします。</span><span class="sxs-lookup"><span data-stu-id="c74ff-103">Applications that handle sensitive data or make any kind of security decisions need to keep that data under their own control and cannot allow other potentially malicious code to access the data directly.</span></span> <span data-ttu-id="c74ff-104">メモリ内でデータを保護する最善の方法は、そのデータをプライベート変数または内部変数 (同じアセンブリにスコープが限定されている) として宣言することです。</span><span class="sxs-lookup"><span data-stu-id="c74ff-104">The best way to protect data in memory is to declare the data as private or internal (with scope limited to the same assembly) variables.</span></span> <span data-ttu-id="c74ff-105">ただし、このようなデータでさえも、次のように注意が必要なアクセスの対象となります。</span><span class="sxs-lookup"><span data-stu-id="c74ff-105">However, even this data is subject to access you should be aware of:</span></span>  
  
-   <span data-ttu-id="c74ff-106">リフレクション メカニズムを使用すると、オブジェクトを参照できる信頼性の高いコードはプライベート メンバーを取得および設定できます。</span><span class="sxs-lookup"><span data-stu-id="c74ff-106">Using reflection mechanisms, highly trusted code that can reference your object can get and set private members.</span></span>  
  
-   <span data-ttu-id="c74ff-107">シリアル化を使用すると、信頼性の高いコードがプライベート メンバーを効率よく取得および設定できます (シリアル化された形式のオブジェクトにおいて対応するデータにアクセスできる場合)。</span><span class="sxs-lookup"><span data-stu-id="c74ff-107">Using serialization, highly trusted code can effectively get and set private members if it can access the corresponding data in the serialized form of the object.</span></span>  
  
-   <span data-ttu-id="c74ff-108">デバッギング中にはこのデータを読み取ることができます。</span><span class="sxs-lookup"><span data-stu-id="c74ff-108">Under debugging, this data can be read.</span></span>  
  
 <span data-ttu-id="c74ff-109">自分のメソッドやプロパティがこれらの値を意図せずに公開することのないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="c74ff-109">Make sure none of your own methods or properties exposes these values unintentionally.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74ff-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="c74ff-110">See Also</span></span>  
 [<span data-ttu-id="c74ff-111">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="c74ff-111">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
