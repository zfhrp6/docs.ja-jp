---
title: "クラスを定義する (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec002e1709fa5fe31dfe7744fb91a230c32337a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-defining-classes-visual-basic"></a>チュートリアル: クラスの定義 (Visual Basic)
このチュートリアルでは、オブジェクトの作成に使用できるクラスを定義する方法を示します。 また、プロパティとメソッドを新しいクラスに追加する方法を説明し、オブジェクトを初期化する方法を示します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-a-class"></a>クラスを定義するには  
  
1.  クリックして、プロジェクトを作成**新しいプロジェクト**上、**ファイル**メニュー。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  Windows アプリケーションを一覧から選択[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プロジェクト テンプレートを新しいプロジェクトを表示します。  
  
3.  クリックして、プロジェクトに新しいクラスを追加**クラスの追加**上、**プロジェクト**メニュー。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
4.  選択、**クラス**テンプレート。  
  
5.  新しいクラスの名前を`UserNameInfo.vb`、順にクリック**追加**新しいクラスのコードを表示します。  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  使用することができます、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **コード エディター** 」と入力して、スタートアップ フォームにクラスを追加する、`Class`キーワードの後に、新しいクラスの名前。 **コード エディター** 、対応する提供`End Class`するステートメント。  
  
6.  間に次のコードを追加することで、クラスのプライベート フィールドを定義、`Class`と`End Class`ステートメント。  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     としてフィールドを宣言する`Private`クラス内でのみ使用できることを意味します。 利用できるフィールドからクラスの外部などのアクセス修飾子を使用して、`Public`以上のアクセスを提供します。 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
7.  次のコードを追加することで、クラスのプロパティを定義します。  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  次のコードを追加することで、クラスのメソッドを定義します。  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. という名前のプロシージャを追加することで、新しいクラスのパラメーター化されたコンス トラクターを定義`Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     `Sub New`コンス トラクターはこのクラスに基づくオブジェクトの作成時に自動的に呼び出されます。 このコンス トラクターは、ユーザー名を格納するフィールドの値を設定します。  
  
### <a name="to-create-a-button-to-test-the-class"></a>クラスをテストするためのボタンを作成するには  
  
1.  スタートアップ フォームをデザイン モードをでその名前を右クリックして変更**ソリューション エクスプ ローラー**クリックし、**ビュー デザイナー**です。 既定では、Windows アプリケーション プロジェクトをスタートアップ フォームに Form1.vb がという名前です。 メイン フォームが表示されます。  
  
2.  メイン フォームにボタンを追加し、ダブルクリックのコードを表示して、`Button1_Click`イベント ハンドラー。 テストのプロシージャを呼び出すには、次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a>アプリケーションを実行するには  
  
1.  F5 キーを押してアプリケーションを実行します。 テストのプロシージャを呼び出してフォーム上のボタンをクリックします。 元のことを示すメッセージを表示`UserName`"MOORE、BOBBY"では、プロシージャを呼び出す、`Capitalize`オブジェクトのメソッドです。  
  
2.  をクリックして**OK**メッセージ ボックスを閉じます。 `Button1 Click`プロシージャの値を変更する、`UserName`プロパティの新しい値のことを示すメッセージを表示および`UserName`"Worden、Joe"は、します。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト指向プログラミング](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)  
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
