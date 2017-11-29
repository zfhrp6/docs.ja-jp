---
title: "&#39; #Region &#39;および &#39; #End Region &#39;ステートメントはメソッド本体に複数行ラムダでは有効ではありません。"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords: BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 614d0c7324bfbf07bc5736c799e8b54937ead081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a>&#39; #Region &#39;および &#39; #End Region &#39;ステートメントはメソッド本体や複数行ラムダでは有効ではありません。
`#Region`ブロックは、クラス、モジュール、または名前空間レベルで宣言する必要があります。 折りたたみ可能な領域が 1 つ以上のプロシージャを含めることができますが、開始日または終了、プロシージャ内でそのことはできません。  
  
 **エラー ID:** BC32025  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  前の手順がで正常終了したことを確認してください、`End Function`または`End Sub`ステートメントです。  
  
2.  いることを確認、`#Region`と`#End Region`ディレクティブが同じコード ブロックではします。  
  
## <a name="see-also"></a>関連項目  
 [#Region ディレクティブ](../../../visual-basic/language-reference/directives/region-directive.md)
