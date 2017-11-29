---
title: "ディレクティブ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8219f17f1b8093b4d02b370c7b008101923b1873
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="directives-visual-basic"></a><span data-ttu-id="08539-102">ディレクティブ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08539-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="08539-103">このセクションのトピックでは、Visual Basic ソース コードのコンパイラ ディレクティブについて説明します。</span><span class="sxs-lookup"><span data-stu-id="08539-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="08539-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="08539-104">In This Section</span></span>  
 <span data-ttu-id="08539-105">[#Const ディレクティブ](../../../visual-basic/language-reference/directives/const-directive.md)--コンパイラ定数の定義</span><span class="sxs-lookup"><span data-stu-id="08539-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="08539-106">[#ExternalSource ディレクティブ](../../../visual-basic/language-reference/directives/externalsource-directive.md)--ソース行と、ソースに外部のテキストの間のマッピングを示します</span><span class="sxs-lookup"><span data-stu-id="08539-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="08539-107">[#If しています.Then... #Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)--選択したコード ブロックをコンパイル</span><span class="sxs-lookup"><span data-stu-id="08539-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="08539-108">[#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)--を折りたたんで、Visual Studio エディターでコードのセクションを非表示にします。</span><span class="sxs-lookup"><span data-stu-id="08539-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="08539-109">**#Disable、#Enable** : を無効にして、コードの領域の特定の警告を有効にします。</span><span class="sxs-lookup"><span data-stu-id="08539-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="08539-110">警告コードのコンマ区切りリストを無効および有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="08539-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="08539-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="08539-111">Related Sections</span></span>  
 [<span data-ttu-id="08539-112">Visual Basic の言語リファレンス</span><span class="sxs-lookup"><span data-stu-id="08539-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="08539-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08539-113">Visual Basic</span></span>](../../../visual-basic/index.md)
