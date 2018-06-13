---
title: -preferreduilang (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 21a3baceb8a46723de1c633e415af0660bb41840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211752"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="648c2-102">-preferreduilang (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="648c2-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="648c2-103">`-preferreduilang` コンパイラ オプションを使うと、C# コンパイラがエラー メッセージなどの出力を表示する言語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="648c2-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="648c2-104">構文</span><span class="sxs-lookup"><span data-stu-id="648c2-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="648c2-105">引数</span><span class="sxs-lookup"><span data-stu-id="648c2-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="648c2-106">コンパイラの出力に使う言語の[言語名](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="648c2-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="648c2-107">コメント</span><span class="sxs-lookup"><span data-stu-id="648c2-107">Remarks</span></span>  
 <span data-ttu-id="648c2-108">`-preferreduilang` コンパイラ オプションを使うと、C# コンパイラがエラー メッセージおよびその他のコマンドライン出力に使う言語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="648c2-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="648c2-109">言語の言語パックがインストールされていない場合は、オペレーティング システムの言語設定が代わりに使われ、エラーは報告されません。</span><span class="sxs-lookup"><span data-stu-id="648c2-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="648c2-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="648c2-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="648c2-111">参照</span><span class="sxs-lookup"><span data-stu-id="648c2-111">See Also</span></span>  
 [<span data-ttu-id="648c2-112">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="648c2-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
