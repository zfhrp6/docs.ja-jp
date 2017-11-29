---
title: "-utf8output (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /utf8output
helpviewer_keywords:
- utf8output compiler option [C#]
- /utf8output compiler option [C#]
- -utf8output compiler option [C#]
ms.assetid: 27ff7381-c281-45d7-b2eb-1ad644b1354e
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 95630afcfcd2ae9ab64660eb0f022dd0733b4c4a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="utf8output-c-compiler-options"></a><span data-ttu-id="8d247-102">/utf8output (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="8d247-102">/utf8output (C# Compiler Options)</span></span>
<span data-ttu-id="8d247-103">**/utf8output** オプションは UTF-8 エンコードを使用してコンパイラ出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="8d247-103">The **/utf8output** option displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d247-104">構文</span><span class="sxs-lookup"><span data-stu-id="8d247-104">Syntax</span></span>  
  
```console  
/utf8output  
```  
  
## <a name="remarks"></a><span data-ttu-id="8d247-105">コメント</span><span class="sxs-lookup"><span data-stu-id="8d247-105">Remarks</span></span>  
 <span data-ttu-id="8d247-106">国際化の設定によっては、コンパイラの出力が正しくコンソールに表示できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="8d247-106">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="8d247-107">これらの設定では、**/utf8output** を使用してコンパイラ出力をファイルにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="8d247-107">In these configurations, use **/utf8output** and redirect compiler output to a file.</span></span>  
  
 <span data-ttu-id="8d247-108">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="8d247-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d247-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="8d247-109">See Also</span></span>  
 [<span data-ttu-id="8d247-110">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="8d247-110">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
