---
title: "do 束縛 (F#)"
description: "使用方法を学習、f# のバインドを ' do' は関数または値を定義することがなくコードを実行します。"
keywords: "visual f#, f#, 関数型プログラミング"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4c1057a3-3aa1-4b64-b46a-25ffe33f0be9
ms.openlocfilehash: f2563d384b67c005c96c2ff487c786476d385e70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="do-bindings"></a><span data-ttu-id="1ee2f-104">do 束縛</span><span class="sxs-lookup"><span data-stu-id="1ee2f-104">do Bindings</span></span>

<span data-ttu-id="1ee2f-105">A`do`バインディングを使用して、関数、または値を定義することがなくコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="1ee2f-105">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="1ee2f-106">、はバインドすることもクラスで使用される、を参照してください[`do`クラス内のバインディング](../members/do-bindings-in-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="1ee2f-106">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="1ee2f-107">構文</span><span class="sxs-lookup"><span data-stu-id="1ee2f-107">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="1ee2f-108">コメント</span><span class="sxs-lookup"><span data-stu-id="1ee2f-108">Remarks</span></span>
<span data-ttu-id="1ee2f-109">使用して、`do`関数、または値の定義とは無関係にコードを実行するときにバインディングします。</span><span class="sxs-lookup"><span data-stu-id="1ee2f-109">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="1ee2f-110">内の式、`do`バインドを返す必要があります`unit`です。</span><span class="sxs-lookup"><span data-stu-id="1ee2f-110">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="1ee2f-111">最上位のコード`do`モジュールが初期化されるときにバインディングを実行します。</span><span class="sxs-lookup"><span data-stu-id="1ee2f-111">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="1ee2f-112">キーワード`do`は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="1ee2f-112">The keyword `do` is optional.</span></span>

<span data-ttu-id="1ee2f-113">属性は、最上位レベルに適用できる`do`バインドします。</span><span class="sxs-lookup"><span data-stu-id="1ee2f-113">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="1ee2f-114">たとえば、プログラムでは、COM 相互運用機能を使用する場合を適用する、`STAThread`属性をプログラムにします。</span><span class="sxs-lookup"><span data-stu-id="1ee2f-114">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="1ee2f-115">こうことで、属性を使用して、`do`バインド、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="1ee2f-115">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="1ee2f-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1ee2f-116">See Also</span></span>
[<span data-ttu-id="1ee2f-117">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="1ee2f-117">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="1ee2f-118">関数</span><span class="sxs-lookup"><span data-stu-id="1ee2f-118">Functions</span></span>](index.md)

