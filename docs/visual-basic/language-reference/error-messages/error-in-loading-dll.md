---
title: DLL 読み込み時のエラーです。(Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cc557dcc6709178b6519adb56f31debcbd1d1c39
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
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
