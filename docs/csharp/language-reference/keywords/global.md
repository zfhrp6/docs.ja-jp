---
title: "global (C# リファレンス)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- global
- global_CSharpKeyword
helpviewer_keywords:
- global keyword [C#]
ms.assetid: 8932c16a-6959-42c2-86e7-2c4221ab788b
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ed2acc7384fbf3825a304888c58658d082858211
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2017
---
# <a name="global-c-reference"></a><span data-ttu-id="f4035-102">global (C# リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f4035-102">global (C# Reference)</span></span>
<span data-ttu-id="f4035-103">[:: 演算子](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)の前に来るとき、`global` コンテキスト キーワードは、C# プログラムの既定の名前空間であるグローバル名前空間を参照し、そうでない場合は名前のないグローバル名前空間を参照します。</span><span class="sxs-lookup"><span data-stu-id="f4035-103">The `global` contextual keyword, when it comes before the [:: operator](../../../csharp/language-reference/operators/namespace-alias-qualifer.md), refers to the global namespace, which is the default namespace for any C# program and is otherwise unnamed.</span></span> <span data-ttu-id="f4035-104">詳細については、「[方法: グローバル名前空間エイリアスを使用する](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f4035-104">For more information, see [How to: Use the Global Namespace Alias](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4035-105">例</span><span class="sxs-lookup"><span data-stu-id="f4035-105">Example</span></span>  
 <span data-ttu-id="f4035-106">次の例では、コンテキスト キーワード `global` を利用し、グローバル名前空間でクラス `TestApp` が定義されることを指定しています。</span><span class="sxs-lookup"><span data-stu-id="f4035-106">The following example shows how to use the `global` contextual keyword to specify that the class `TestApp` is defined in the global namespace:</span></span>  
  
 [!code-csharp[csrefKeywordsContextual#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/global_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f4035-107">関連項目</span><span class="sxs-lookup"><span data-stu-id="f4035-107">See Also</span></span>  
 [<span data-ttu-id="f4035-108">名前空間</span><span class="sxs-lookup"><span data-stu-id="f4035-108">Namespaces</span></span>](../../../csharp/programming-guide/namespaces/index.md)
