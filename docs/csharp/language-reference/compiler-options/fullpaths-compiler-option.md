---
title: "-fullpaths (C# コンパイラ オプション)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /fullpaths
dev_langs:
- CSharp
helpviewer_keywords:
- /fullpaths compiler option [C#]
- absolute paths [C#]
- fullpaths compiler option [C#]
- full paths [C#]
- -fullpaths compiler option [C#]
ms.assetid: d2a5f857-cbb2-430b-879c-d648aaf0b8c4
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
ms.openlocfilehash: abd78253c44ae1c90241b2ff2bd236513a846384
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="fullpaths-c-compiler-options"></a><span data-ttu-id="4102b-102">/fullpaths (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="4102b-102">/fullpaths (C# Compiler Options)</span></span>
<span data-ttu-id="4102b-103">**/fullpaths** オプションを指定すると、コンパイルのエラーや警告を一覧表示するとき、コンパイラはファイルの完全なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="4102b-103">The **/fullpaths** option causes the compiler to specify the full path to the file when listing compilation errors and warnings.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4102b-104">構文</span><span class="sxs-lookup"><span data-stu-id="4102b-104">Syntax</span></span>  
  
```console  
/fullpaths  
```  
  
## <a name="remarks"></a><span data-ttu-id="4102b-105">コメント</span><span class="sxs-lookup"><span data-stu-id="4102b-105">Remarks</span></span>  
 <span data-ttu-id="4102b-106">既定では、コンパイルの結果として発生したエラーや警告には、エラーが見つかったファイルの名前が指定されます。</span><span class="sxs-lookup"><span data-stu-id="4102b-106">By default, errors and warnings that result from compilation specify the name of the file in which an error was found.</span></span> <span data-ttu-id="4102b-107">**/fullpaths** オプションを指定すると、コンパイラはファイルの完全なパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="4102b-107">The **/fullpaths** option causes the compiler to specify the full path to the file.</span></span>  
  
 <span data-ttu-id="4102b-108">このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。</span><span class="sxs-lookup"><span data-stu-id="4102b-108">This compiler option is unavailable in Visual Studio and cannot be changed programmatically.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4102b-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="4102b-109">See Also</span></span>  
 [<span data-ttu-id="4102b-110">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="4102b-110">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)

