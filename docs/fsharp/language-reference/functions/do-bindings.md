---
title: do 束縛 (F#)
description: 使用方法を学習、f# のバインドを ' do' は関数または値を定義することがなくコードを実行します。
ms.date: 05/16/2016
ms.openlocfilehash: 6fd084090a204beab0da1c2deb5b5ae2a86281c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="do-bindings"></a><span data-ttu-id="3688c-103">do 束縛</span><span class="sxs-lookup"><span data-stu-id="3688c-103">do Bindings</span></span>

<span data-ttu-id="3688c-104">A`do`バインディングを使用して、関数、または値を定義することがなくコードを実行します。</span><span class="sxs-lookup"><span data-stu-id="3688c-104">A `do` binding is used to execute code without defining a function or value.</span></span> <span data-ttu-id="3688c-105">、はバインドすることもクラスで使用される、を参照してください[`do`クラス内のバインディング](../members/do-bindings-in-classes.md)です。</span><span class="sxs-lookup"><span data-stu-id="3688c-105">Also, do bindings can be used in classes, see [`do` Bindings in Classes](../members/do-bindings-in-classes.md).</span></span>


## <a name="syntax"></a><span data-ttu-id="3688c-106">構文</span><span class="sxs-lookup"><span data-stu-id="3688c-106">Syntax</span></span>

```fsharp
[ attributes ]
[ do ]expression
```

## <a name="remarks"></a><span data-ttu-id="3688c-107">コメント</span><span class="sxs-lookup"><span data-stu-id="3688c-107">Remarks</span></span>
<span data-ttu-id="3688c-108">使用して、`do`関数、または値の定義とは無関係にコードを実行するときにバインディングします。</span><span class="sxs-lookup"><span data-stu-id="3688c-108">Use a `do` binding when you want to execute code independently of a function or value definition.</span></span> <span data-ttu-id="3688c-109">内の式、`do`バインドを返す必要があります`unit`です。</span><span class="sxs-lookup"><span data-stu-id="3688c-109">The expression in a `do` binding must return `unit`.</span></span> <span data-ttu-id="3688c-110">最上位のコード`do`モジュールが初期化されるときにバインディングを実行します。</span><span class="sxs-lookup"><span data-stu-id="3688c-110">Code in a top-level `do` binding is executed when the module is initialized.</span></span> <span data-ttu-id="3688c-111">キーワード`do`は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="3688c-111">The keyword `do` is optional.</span></span>

<span data-ttu-id="3688c-112">属性は、最上位レベルに適用できる`do`バインドします。</span><span class="sxs-lookup"><span data-stu-id="3688c-112">Attributes can be applied to a top-level `do` binding.</span></span> <span data-ttu-id="3688c-113">たとえば、プログラムでは、COM 相互運用機能を使用する場合を適用する、`STAThread`属性をプログラムにします。</span><span class="sxs-lookup"><span data-stu-id="3688c-113">For example, if your program uses COM interop, you might want to apply the `STAThread` attribute to your program.</span></span> <span data-ttu-id="3688c-114">こうことで、属性を使用して、`do`バインド、次のコードに示すようにします。</span><span class="sxs-lookup"><span data-stu-id="3688c-114">You can do this by using an attribute on a `do` binding, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet201.fs)]
    
## <a name="see-also"></a><span data-ttu-id="3688c-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3688c-115">See Also</span></span>
[<span data-ttu-id="3688c-116">F# 言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="3688c-116">F# Language Reference</span></span>](../index.md)

[<span data-ttu-id="3688c-117">関数</span><span class="sxs-lookup"><span data-stu-id="3688c-117">Functions</span></span>](index.md)

