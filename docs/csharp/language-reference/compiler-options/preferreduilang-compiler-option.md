---
title: "-preferreduilang (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a96a054b3d1f73b0fee209557388f7ea213ebbe9
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2017
---
# <a name="preferreduilang-c-compiler-options"></a><span data-ttu-id="a1930-102">/preferreduilang (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="a1930-102">/preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="a1930-103">`/preferreduilang` コンパイラ オプションを使うと、C# コンパイラがエラー メッセージなどの出力を表示する言語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1930-103">By using the `/preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1930-104">構文</span><span class="sxs-lookup"><span data-stu-id="a1930-104">Syntax</span></span>  
  
```console  
/preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="a1930-105">引数</span><span class="sxs-lookup"><span data-stu-id="a1930-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="a1930-106">コンパイラの出力に使う言語の[言語名](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="a1930-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1930-107">コメント</span><span class="sxs-lookup"><span data-stu-id="a1930-107">Remarks</span></span>  
 <span data-ttu-id="a1930-108">`/preferreduilang` コンパイラ オプションを使うと、C# コンパイラがエラー メッセージおよびその他のコマンドライン出力に使う言語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1930-108">You can use the `/preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="a1930-109">言語の言語パックがインストールされていない場合は、オペレーティング システムの言語設定が代わりに使われ、エラーは報告されません。</span><span class="sxs-lookup"><span data-stu-id="a1930-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="a1930-110">要件</span><span class="sxs-lookup"><span data-stu-id="a1930-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1930-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="a1930-111">See Also</span></span>  
 [<span data-ttu-id="a1930-112">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="a1930-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
