---
title: "-preferreduilang (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4fcf075dd951d733d294a62de98365c77b16a51d
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="ba00d-102">-preferreduilang (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="ba00d-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="ba00d-103">`-preferreduilang` コンパイラ オプションを使うと、C# コンパイラがエラー メッセージなどの出力を表示する言語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ba00d-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba00d-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba00d-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="ba00d-105">引数</span><span class="sxs-lookup"><span data-stu-id="ba00d-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="ba00d-106">コンパイラの出力に使う言語の[言語名](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx)。</span><span class="sxs-lookup"><span data-stu-id="ba00d-106">The [language name](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba00d-107">コメント</span><span class="sxs-lookup"><span data-stu-id="ba00d-107">Remarks</span></span>  
 <span data-ttu-id="ba00d-108">`-preferreduilang` コンパイラ オプションを使うと、C# コンパイラがエラー メッセージおよびその他のコマンドライン出力に使う言語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="ba00d-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="ba00d-109">言語の言語パックがインストールされていない場合は、オペレーティング システムの言語設定が代わりに使われ、エラーは報告されません。</span><span class="sxs-lookup"><span data-stu-id="ba00d-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="ba00d-110">必要条件</span><span class="sxs-lookup"><span data-stu-id="ba00d-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba00d-111">参照</span><span class="sxs-lookup"><span data-stu-id="ba00d-111">See Also</span></span>  
 [<span data-ttu-id="ba00d-112">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="ba00d-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
