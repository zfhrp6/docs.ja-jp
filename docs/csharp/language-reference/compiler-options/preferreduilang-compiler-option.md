---
title: "-preferreduilang (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /preferreduilang
dev_langs:
- CSharp
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: b94c2794642ad93a78eaafdeb655310e4ecb2d25
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="preferreduilang-c-compiler-options"></a><span data-ttu-id="906f9-102">/preferreduilang (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="906f9-102">/preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="906f9-103">`/preferreduilang` コンパイラ オプションを使うと、C# コンパイラがエラー メッセージなどの出力を表示する言語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="906f9-103">By using the `/preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="906f9-104">構文</span><span class="sxs-lookup"><span data-stu-id="906f9-104">Syntax</span></span>  
  
```console  
/preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="906f9-105">引数</span><span class="sxs-lookup"><span data-stu-id="906f9-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="906f9-106">コンパイラの出力に使う言語の[言語名](http://go.microsoft.com/fwlink/p/?LinkId=236992)。</span><span class="sxs-lookup"><span data-stu-id="906f9-106">The [language name](http://go.microsoft.com/fwlink/p/?LinkId=236992) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="906f9-107">コメント</span><span class="sxs-lookup"><span data-stu-id="906f9-107">Remarks</span></span>  
 <span data-ttu-id="906f9-108">`/preferreduilang` コンパイラ オプションを使うと、C# コンパイラがエラー メッセージおよびその他のコマンドライン出力に使う言語を指定できます。</span><span class="sxs-lookup"><span data-stu-id="906f9-108">You can use the `/preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="906f9-109">言語の言語パックがインストールされていない場合は、オペレーティング システムの言語設定が代わりに使われ、エラーは報告されません。</span><span class="sxs-lookup"><span data-stu-id="906f9-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe /preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="906f9-110">要件</span><span class="sxs-lookup"><span data-stu-id="906f9-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="906f9-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="906f9-111">See Also</span></span>  
 [<span data-ttu-id="906f9-112">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="906f9-112">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

