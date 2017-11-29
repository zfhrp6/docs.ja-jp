---
title: "Visual Basic におけるオブジェクト変数"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44689d649a381618e5d6c934deb2b7b9bea463ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="object-variables-in-visual-basic"></a>Visual Basic におけるオブジェクト変数
値を直接格納だけでなく、変数は、オブジェクトを参照できます。 同じ理由から、変数に任意の値を代入するには、変数にオブジェクトを割り当てます。  
  
-   変数名は、多くの場合、メソッドと、オブジェクト自体にアクセスするために必要なプロパティの完全なパスよりも覚えやすくを短くします。  
  
-   オブジェクトを参照する変数を使用するは、繰り返しの必要なメソッドやプロパティを使って、オブジェクト自体にアクセスするよりも効率的です。  
  
-   コードの実行中に、その他のオブジェクトを参照する変数を変更することができます。  
  
## <a name="making-code-shorter"></a>コードを短く  
 オブジェクト変数を使用すると、入力するのに必要があるコードを短縮します。 次の例にアクセスするメソッドとプロパティの完全なパスを使用して、<xref:System.Windows.Forms.Control>オブジェクト。  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 このコードを短縮し、コントロールのオブジェクト変数を使用する場合、実行を高速化できます。 特定のクラスに割り当てるしようとするオブジェクト変数を宣言する必要があります (`Control`ここで)。 オブジェクトを変数に代入するとに参照するオブジェクトを処理するとまったく同じように扱うことできます。 設定またはオブジェクトのプロパティを取得したり独自のメソッドのいずれかを使用できます。 次の例では、オブジェクト変数を使用して、前の例のコードを簡略化します。  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a>関連項目  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [方法 : 長い修飾パスを持つオブジェクトへのアクセス時間を短縮する](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [オブジェクト変数の宣言](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
