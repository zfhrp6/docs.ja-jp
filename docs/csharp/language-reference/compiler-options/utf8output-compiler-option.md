---
title: "-utf8output (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /utf8output
dev_langs:
- CSharp
helpviewer_keywords:
- utf8output compiler option [C#]
- /utf8output compiler option [C#]
- -utf8output compiler option [C#]
ms.assetid: 27ff7381-c281-45d7-b2eb-1ad644b1354e
caps.latest.revision: 10
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
ms.openlocfilehash: 11f79ee8c64c8331f75ac021f10de8c5f54728f6
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="utf8output-c-compiler-options"></a><span data-ttu-id="e95a6-102">/utf8output (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="e95a6-102">/utf8output (C# Compiler Options)</span></span>
<span data-ttu-id="e95a6-103">**/utf8output** オプションは UTF-8 エンコードを使用してコンパイラ出力を表示します。</span><span class="sxs-lookup"><span data-stu-id="e95a6-103">The **/utf8output** option displays compiler output using UTF-8 encoding.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e95a6-104">構文</span><span class="sxs-lookup"><span data-stu-id="e95a6-104">Syntax</span></span>  
  
```console  
/utf8output  
```  
  
## <a name="remarks"></a><span data-ttu-id="e95a6-105">コメント</span><span class="sxs-lookup"><span data-stu-id="e95a6-105">Remarks</span></span>  
 <span data-ttu-id="e95a6-106">国際化の設定によっては、コンパイラの出力が正しくコンソールに表示できない場合があります。</span><span class="sxs-lookup"><span data-stu-id="e95a6-106">In some international configurations, compiler output cannot correctly be displayed in the console.</span></span> <span data-ttu-id="e95a6-107">これらの設定では、**/utf8output** を使用してコンパイラ出力をファイルにリダイレクトします。</span><span class="sxs-lookup"><span data-stu-id="e95a6-107">In these configurations, use **/utf8output** and redirect compiler output to a file.</span></span>  
  
 <span data-ttu-id="e95a6-108">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="e95a6-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e95a6-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="e95a6-109">See Also</span></span>  
 [<span data-ttu-id="e95a6-110">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="e95a6-110">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

