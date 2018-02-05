---
title: "方法 : ユーザー定義の例外を作成する"
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
- cpp
helpviewer_keywords:
- user-defined exceptions
- exceptions, examples
- exceptions, user-defined
ms.assetid: 25819a5a-f915-4fc8-b924-a76915674e04
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c55489a4c0b86142fcda99c5962c896b73691cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-user-defined-exceptions"></a><span data-ttu-id="0c29a-102">ユーザー定義の例外を作成する方法</span><span class="sxs-lookup"><span data-stu-id="0c29a-102">How to create user-defined exceptions</span></span>

<span data-ttu-id="0c29a-103">.NET では、基底クラス <xref:System.Exception> から最終的に派生した例外クラスの階層構造を提供します。</span><span class="sxs-lookup"><span data-stu-id="0c29a-103">.NET provides a hierarchy of exception classes ultimately derived from the base class <xref:System.Exception>.</span></span> <span data-ttu-id="0c29a-104">ただし、定義済みの例外のいずれも要件を満たさない場合は、<xref:System.Exception> クラスから派生することによって、独自の例外クラスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="0c29a-104">However, if none of the predefined exceptions meets your needs, you can create your own exception classes by deriving from the <xref:System.Exception> class.</span></span>

<span data-ttu-id="0c29a-105">独自の例外を作成するときに、ユーザー定義の例外のクラス名の末尾に "Exception" という単語を付加し、次の例で示すように、3 つの共通コンストラクターを実装します。</span><span class="sxs-lookup"><span data-stu-id="0c29a-105">When creating your own exceptions, end the class name of the user-defined exception with the word "Exception," and implement the three common constructors, as shown in the following example.</span></span> <span data-ttu-id="0c29a-106">例では、`EmployeeListNotFoundException` という名前の新しい例外クラスを定義します。</span><span class="sxs-lookup"><span data-stu-id="0c29a-106">The example defines a new exception class named `EmployeeListNotFoundException`.</span></span> <span data-ttu-id="0c29a-107">このクラスは <xref:System.Exception> から派生し、次の 3 つのコンストラクターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="0c29a-107">The class is derived from <xref:System.Exception> and includes three constructors.</span></span>

[!code-cpp[dg_exceptionDesign#14](../../../samples/snippets/cpp/VS_Snippets_CLR/dg_exceptionDesign/cpp/example2.cpp#14)]
[!code-csharp[dg_exceptionDesign#14](../../../samples/snippets/csharp/VS_Snippets_CLR/dg_exceptionDesign/cs/example2.cs#14)]
[!code-vb[dg_exceptionDesign#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/dg_exceptionDesign/vb/example2.vb#14)]  

> [!NOTE]
> <span data-ttu-id="0c29a-108">リモート処理を使用している場合は、任意のユーザー定義の例外のメタデータがサーバー側 (呼び出し先) とクライアント (プロキシ オブジェクトまたは呼び出し元) で使用できることを保証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="0c29a-108">In situations where you are using remoting, you must ensure that the metadata for any user-defined exceptions is available at the server (callee) and to the client (the proxy object or caller).</span></span> <span data-ttu-id="0c29a-109">詳細については、「[例外の推奨事項](best-practices-for-exceptions.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c29a-109">For more information, see [Best practices for exceptions](best-practices-for-exceptions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0c29a-110">参照</span><span class="sxs-lookup"><span data-stu-id="0c29a-110">See Also</span></span>  
[<span data-ttu-id="0c29a-111">例外</span><span class="sxs-lookup"><span data-stu-id="0c29a-111">Exceptions</span></span>](index.md)
