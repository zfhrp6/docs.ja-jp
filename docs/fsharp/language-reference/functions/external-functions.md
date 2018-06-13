---
title: 外部関数 (F#)
description: ネイティブ コードで関数の呼び出しの f# 言語サポートについて説明します。
ms.date: 05/16/2016
ms.openlocfilehash: 398697c5e0deab7f8d81ec5198ab1918bd865e13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564483"
---
# <a name="external-functions"></a><span data-ttu-id="0b60a-103">外部関数</span><span class="sxs-lookup"><span data-stu-id="0b60a-103">External Functions</span></span>

<span data-ttu-id="0b60a-104">このトピックでは、ネイティブ コードで関数の呼び出しの f# 言語サポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="0b60a-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="0b60a-105">構文</span><span class="sxs-lookup"><span data-stu-id="0b60a-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="0b60a-106">コメント</span><span class="sxs-lookup"><span data-stu-id="0b60a-106">Remarks</span></span>

<span data-ttu-id="0b60a-107">前の構文で*引数*に渡される引数を表す、`System.Runtime.InteropServices.DllImportAttribute`属性。</span><span class="sxs-lookup"><span data-stu-id="0b60a-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="0b60a-108">最初の引数は、.dll 拡張子を除いた、この関数を含んでいる DLL の名前を表す文字列です。</span><span class="sxs-lookup"><span data-stu-id="0b60a-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="0b60a-109">いずれかのパブリック プロパティの追加の引数を指定することができます、`System.Runtime.InteropServices.DllImportAttribute`クラス、呼び出し規則などです。</span><span class="sxs-lookup"><span data-stu-id="0b60a-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="0b60a-110">ネイティブ C++ の DLL を次のエクスポート関数を含む必要があると仮定します。</span><span class="sxs-lookup"><span data-stu-id="0b60a-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="0b60a-111">次のコードを使用して、F# からこの関数を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="0b60a-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="0b60a-112">ネイティブ コードとの相互運用性と呼びます*プラットフォーム呼び出し*あり、CLR の機能です。</span><span class="sxs-lookup"><span data-stu-id="0b60a-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="0b60a-113">詳細については、「[アンマネージ コードとの相互運用](../../../../docs/framework/interop/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b60a-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="0b60a-114">そのセクションの情報は、f# に適用されます。</span><span class="sxs-lookup"><span data-stu-id="0b60a-114">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="0b60a-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b60a-115">See Also</span></span>

[<span data-ttu-id="0b60a-116">関数</span><span class="sxs-lookup"><span data-stu-id="0b60a-116">Functions</span></span>](index.md)
