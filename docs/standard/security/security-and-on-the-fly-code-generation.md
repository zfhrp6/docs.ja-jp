---
title: "セキュリティと実行時のコード生成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c6bb895979fb44616349505a07591f9ced9fedac
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="b2c62-102">セキュリティと実行時のコード生成</span><span class="sxs-lookup"><span data-stu-id="b2c62-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="b2c62-103">ライブラリによっては、コードを生成し、それを実行することによって、呼び出し元のためになんらかの処理を行います。</span><span class="sxs-lookup"><span data-stu-id="b2c62-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="b2c62-104">基本的に問題となるのは、より低い信頼度のコードの代わりに生成し、そのコードをより高い信頼度で実行することです。</span><span class="sxs-lookup"><span data-stu-id="b2c62-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="b2c62-105">呼び出し側がコードの生成に影響を及ぼすと問題はさらに悪化するため、安全と考えられるコードだけが生成されることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b2c62-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="b2c62-106">常に、どのようなコードが生成されているのかを知る必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2c62-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="b2c62-107">これは、ユーザーから取得する値を厳しく制御することが必要であることを意味します。これらの値は、引用符で囲まれた文字列、ID、またはそれ以外です。引用符で囲まれた文字列は予期しないコード要素を含まないようにエスケープ処理が必要で、ID は有効な ID かどうかをチェックする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2c62-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="b2c62-108">コンパイルされたアセンブリは変更できるため、変更によってその ID に異常な文字が含まれると、セキュリティが脅かされます。このため、ID にも危険性があります。ただし、これがセキュリティ脆弱性になることは稀です。</span><span class="sxs-lookup"><span data-stu-id="b2c62-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="b2c62-109">リフレクション出力を指定してコードを生成することをお勧めします。これは、上記の多くの問題を防ぐのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="b2c62-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="b2c62-110">コードをコンパイルするときに、悪意のあるプログラムがなんらかの方法でコードを変更できるかどうかを考慮します。</span><span class="sxs-lookup"><span data-stu-id="b2c62-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="b2c62-111">コンパイラがソース コードを読み取る前、またはコードが .dll を読み込む前に、悪意のあるコードがソース コードを変更できる時間的なすきまがないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b2c62-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="b2c62-112">ある場合は、ファイル システムのアクセス制御リストを適切に使用して、これらのファイルが格納されているディレクトリを保護する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b2c62-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2c62-113">参照</span><span class="sxs-lookup"><span data-stu-id="b2c62-113">See Also</span></span>  
 [<span data-ttu-id="b2c62-114">安全なコーディングのガイドライン</span><span class="sxs-lookup"><span data-stu-id="b2c62-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
