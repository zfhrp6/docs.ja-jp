---
title: "方法: 値の変わらない変数を作成する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d1475553e64fef92ec3f3bb7e1b4fbfb357dbec8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a>方法: 値の変わらない変数を作成する (Visual Basic)
その値が変化しない変数の概念は、矛盾する可能性があります。 定数は実行可能でない場合もありますし、固定値を持つ変数を使用すると便利です。 このようなケースで付きのメンバー変数を定義することができます、 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)キーワード。  
  
 使用することはできません、 [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)宣言して、次の状況に、定数値を代入します。  
  
-   `Const`ステートメントには、使用するデータ型は受け入れません。  
  
-   コンパイル時に値がわからない  
  
-   コンパイル時に定数値を計算できません。  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a>値の変わらない変数を作成するには  
  
1.  モジュール レベルでのメンバー変数を宣言、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)、含めると、 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)キーワード。  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     指定できます`ReadOnly`メンバー変数に対してのみです。 つまり、すべてのプロシージャの外部でのモジュール レベル変数を定義する必要があります。  
  
2.  コンパイル時に単一のステートメントで値を計算する場合で初期化句を使用して、`Dim`ステートメントです。 以下の[として](../../../../visual-basic/language-reference/statements/as-clause.md)等号 (=) を含む句 (`=`)、式でその後にします。 必ず、コンパイラは定数値には、この式を評価できます。  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     値を割り当てることができます、`ReadOnly`変数を一度だけです。 これを行うと、コードが変更できるなしの値。  
  
     、コンパイル時に値がわからないか単一のステートメントでは、コンパイル時に計算できない場合は、コンス トラクターで実行時にも割り当てることができます。 これを行うには、宣言する必要があります、`ReadOnly`クラスまたは構造体のレベルで変数。 そのクラスまたは構造体のコンス トラクターで、変数の固定値を計算し、コンス トラクターから戻る前に、変数に割り当てます。  
  
## <a name="see-also"></a>関連項目  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Const ステートメント](../../../../visual-basic/language-reference/statements/const-statement.md)
