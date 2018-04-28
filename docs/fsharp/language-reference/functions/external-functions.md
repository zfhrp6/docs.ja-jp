---
title: 外部関数 (F#)
description: ネイティブ コードで関数の呼び出しの f# 言語サポートについて説明します。
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 28e74258d91ff2d9742caa7a6c06f515cd987c0a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="external-functions"></a><span data-ttu-id="f63f9-103">外部関数</span><span class="sxs-lookup"><span data-stu-id="f63f9-103">External Functions</span></span>

<span data-ttu-id="f63f9-104">このトピックでは、ネイティブ コードで関数の呼び出しの f# 言語サポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f63f9-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="f63f9-105">構文</span><span class="sxs-lookup"><span data-stu-id="f63f9-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="f63f9-106">コメント</span><span class="sxs-lookup"><span data-stu-id="f63f9-106">Remarks</span></span>

<span data-ttu-id="f63f9-107">前の構文で*引数*に渡される引数を表す、`System.Runtime.InteropServices.DllImportAttribute`属性。</span><span class="sxs-lookup"><span data-stu-id="f63f9-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="f63f9-108">最初の引数は、.dll 拡張子を除いた、この関数を含んでいる DLL の名前を表す文字列です。</span><span class="sxs-lookup"><span data-stu-id="f63f9-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="f63f9-109">いずれかのパブリック プロパティの追加の引数を指定することができます、`System.Runtime.InteropServices.DllImportAttribute`クラス、呼び出し規則などです。</span><span class="sxs-lookup"><span data-stu-id="f63f9-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="f63f9-110">ネイティブ C++ の DLL を次のエクスポート関数を含む必要があると仮定します。</span><span class="sxs-lookup"><span data-stu-id="f63f9-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="f63f9-111">次のコードを使用して、F# からこの関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f63f9-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="f63f9-112">ネイティブ コードとの相互運用性と呼びます*プラットフォーム呼び出し*あり、CLR の機能です。</span><span class="sxs-lookup"><span data-stu-id="f63f9-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="f63f9-113">詳細については、「[アンマネージ コードとの相互運用](../../../../docs/framework/interop/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f63f9-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="f63f9-114">そのセクションの情報は、f# に適用されます。</span><span class="sxs-lookup"><span data-stu-id="f63f9-114">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="f63f9-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="f63f9-115">See Also</span></span>

[<span data-ttu-id="f63f9-116">関数</span><span class="sxs-lookup"><span data-stu-id="f63f9-116">Functions</span></span>](index.md)
