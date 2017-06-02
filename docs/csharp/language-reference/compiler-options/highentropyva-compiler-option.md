---
title: "-highentropyva (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /highentropyva
dev_langs:
- CSharp
helpviewer_keywords:
- /highentropyva compiler option [C#]
- -highentropyva compiler option [C#]
- highentropyva compiler option [C#]
ms.assetid: eaf409b3-384e-49dd-9417-62453658f421
caps.latest.revision: 8
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c1b49faa2fb388b330c24bdff28d00872828b110
ms.contentlocale: ja-jp
ms.lasthandoff: 03/13/2017

---
# <a name="highentropyva-c-compiler-options"></a>/highentropyva (C# コンパイラ オプション)
**/highentropyva** コンパイラ オプションは、特定の実行可能ファイルで高エントロピ ASLR (Address Space Layout Randomization) をサポートするかどうかを Windows カーネルに示します。  
  
## <a name="syntax"></a>構文  
  
```console  
/highentropyva[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 このオプションは、64 ビットの実行可能ファイルまたは [/platform:anycpu](../../../csharp/language-reference/compiler-options/platform-compiler-option.md) コンパイラ オプションによって示される実行可能ファイルで、高エントロピ仮想アドレス空間をサポートすることを指定します。 既定では、このオプションが無効になっています。 有効にするには、**/highentropyva+** または **/highentropyva** を使用してください。  
  
## <a name="remarks"></a>コメント  
 **/highentropyva** オプションを指定すると、適合するバージョンの Windows カーネルで、ASLR の一環としてプロセスのアドレス空間レイアウトをランダム化する際、より高いエントロピを使用できるようになります。 より高いエントロピを使うということは、スタックやヒープといったメモリ領域に割り当てることのできるアドレス数が増えることを意味します。 これによって特定のメモリ領域の位置を推測しづらくなる効果が得られます。  
  
 **/highentropyva** コンパイラ オプションが指定された場合、対象となる実行可能ファイルとその依存モジュールは、64 ビット プロセスとして動作する際に 4 ギガバイト (GB) を超えるポインター値を処理できることが必要です。
