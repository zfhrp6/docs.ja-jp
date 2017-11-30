---
title: "方法 : Visual Basic でオブジェクト変数を宣言し、オブジェクト変数にオブジェクトを代入する"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], declaring
- declaring object variables [Visual Basic]
ms.assetid: 2fa77dde-1fb2-439a-80d4-3e9787649fad
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f4a682c7ae32ace0b1f859d52963342546a83f29
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-an-object-variable-and-assign-an-object-to-it-in-visual-basic"></a>方法 : Visual Basic でオブジェクト変数を宣言し、オブジェクト変数にオブジェクトを代入する
変数を宣言する、[オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)を指定して`As Object`で、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)です。 等号の後、オブジェクトを配置することによってこのような変数にオブジェクトを割り当てる (`=`) 代入ステートメントまたは初期化句でします。  
  
## <a name="example"></a>例  
 次の例で、`Object`変数と、現在のインスタンスに割り当てられます。  
  
```  
      Dim thisObject As Object  
thisObject = "This is an Object"  
```  
  
 宣言と割り当てを結合するには、宣言の一部として変数を初期化します。 次の例では、上記の例と同じです。  
  
```  
Dim thisObject As Object= "This is an Object"  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   <xref:System> 名前空間への参照  
  
-   クラス、構造体、または配置するモジュール、`Dim`ステートメントです。  
  
-   代入ステートメントを記述するためのプロシージャです。  
  
## <a name="see-also"></a>関連項目  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
