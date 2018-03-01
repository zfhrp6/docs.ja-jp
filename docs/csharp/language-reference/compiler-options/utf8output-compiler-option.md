---
title: "-utf8output (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /utf8output
helpviewer_keywords:
- utf8output compiler option [C#]
- /utf8output compiler option [C#]
- -utf8output compiler option [C#]
ms.assetid: 27ff7381-c281-45d7-b2eb-1ad644b1354e
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3716445cb779e98f777a1677ff67e1ba603c5fa2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-utf8output-c-compiler-options"></a><span data-ttu-id="5748c-102">-utf8output (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="5748c-102">-utf8output (C# Compiler Options)</span></span>
<span data-ttu-id="5748c-103">**-utf8output** オプションは UTF-8 エンコードを使用してコンパイラ出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="5748c-103">The **-utf8output** option displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5748c-104">構文</span><span class="sxs-lookup"><span data-stu-id="5748c-104">Syntax</span></span>  
  
```console  
-utf8output  
```  
  
## <a name="remarks"></a><span data-ttu-id="5748c-105">コメント</span><span class="sxs-lookup"><span data-stu-id="5748c-105">Remarks</span></span>  
 <span data-ttu-id="5748c-106">国際化の設定によっては、コンパイラの出力が正しくコンソールに表示できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="5748c-106">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="5748c-107">これらの設定では、**-utf8output** を使用してコンパイラ出力をファイルにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="5748c-107">In these configurations, use **-utf8output** and redirect compiler output to a file.</span></span>  
  
 <span data-ttu-id="5748c-108">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="5748c-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5748c-109">参照</span><span class="sxs-lookup"><span data-stu-id="5748c-109">See Also</span></span>  
 [<span data-ttu-id="5748c-110">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="5748c-110">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
