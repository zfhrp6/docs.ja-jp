---
title: DLL 読み込み時のエラーです。(Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: ac21c4d52b248025ee26bac3e511bb5b0a0b668e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33584684"
---
# <a name="error-in-loading-dll-visual-basic"></a>DLL 読み込み時のエラーです。(Visual Basic)
ダイナミック リンク ライブラリ (DLL) で指定したライブラリは、`Lib`の句、`Declare`ステートメントです。 このエラーの考えられる原因は次のとおりです。  
  
-   ファイルは、DLL の実行可能ファイルではありません。  
  
-   ファイルは、Microsoft Windows DLL ではありません。  
  
-   DLL が存在しない別の DLL を参照します。  
  
-   DLL または参照される DLL がパスに指定されたディレクトリではありません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ファイルが、ソース テキスト ファイルであり、DLL が実行可能の場合は、コンパイルされ、DLL の実行可能ファイルのフォームにリンクする必要があります。  
  
-   ファイルが Microsoft Windows DLL でない場合は、同等の Microsoft Windows を入手します。  
  
-   DLL が存在しない別の DLL を参照する場合は、参照される DLL を入手して使用できるようにします。  
  
-   DLL または参照される DLL がパスで指定されたディレクトリにない場合は、DLL を参照先のディレクトリに移動します。  
  
## <a name="see-also"></a>関連項目  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)
