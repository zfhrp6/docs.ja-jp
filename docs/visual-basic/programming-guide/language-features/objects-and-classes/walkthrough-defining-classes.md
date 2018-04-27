---
title: クラスを定義する (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
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
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9fc173ad853755c4b02a13abc0a80229bebffe64
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-defining-classes-visual-basic"></a>チュートリアル: クラスの定義 (Visual Basic)

このチュートリアルでは、オブジェクトの作成に使用できるクラスを定義する方法を示します。 また、プロパティとメソッドを新しいクラスに追加する方法を説明し、オブジェクトを初期化する方法を示します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>クラスを定義するには
  
1.  クリックして、プロジェクトを作成**新しいプロジェクト**上、**ファイル**メニュー。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  新しいプロジェクトを表示する Visual Basic プロジェクト テンプレートの一覧から Windows アプリケーションを選択します。  
  
3.  クリックして、プロジェクトに新しいクラスを追加**クラスの追加**上、**プロジェクト**メニュー。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
4.  選択、**クラス**テンプレート。  
  
5.  新しいクラスの名前を`UserNameInfo.vb`、順にクリック**追加**新しいクラスのコードを表示します。  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  Visual Basic を使用する**コード エディター** 」と入力して、スタートアップ フォームにクラスを追加する、`Class`キーワードの後に、新しいクラスの名前。 **コード エディター** 、対応する提供`End Class`するステートメント。  
  
6.  間に次のコードを追加することで、クラスのプライベート フィールドを定義、`Class`と`End Class`ステートメント。  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     としてフィールドを宣言する`Private`クラス内でのみ使用できることを意味します。 利用できるフィールドからクラスの外部などのアクセス修飾子を使用して、`Public`以上のアクセスを提供します。 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
7.  次のコードを追加することで、クラスのプロパティを定義します。  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8.  次のコードを追加することで、クラスのメソッドを定義します。  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. という名前のプロシージャを追加することで、新しいクラスのパラメーター化されたコンス トラクターを定義`Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New`コンス トラクターはこのクラスに基づくオブジェクトの作成時に自動的に呼び出されます。 このコンス トラクターは、ユーザー名を格納するフィールドの値を設定します。  
  
## <a name="to-create-a-button-to-test-the-class"></a>クラスをテストするためのボタンを作成するには
  
1.  スタートアップ フォームをデザイン モードをでその名前を右クリックして変更**ソリューション エクスプ ローラー**クリックし、**ビュー デザイナー**です。 既定では、Windows アプリケーション プロジェクトをスタートアップ フォームに Form1.vb がという名前です。 メイン フォームが表示されます。  
  
2.  メイン フォームにボタンを追加し、ダブルクリックのコードを表示して、`Button1_Click`イベント ハンドラー。 テストのプロシージャを呼び出すには、次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>アプリケーションを実行するには
  
1.  F5 キーを押してアプリケーションを実行します。 テストのプロシージャを呼び出してフォーム上のボタンをクリックします。 元のことを示すメッセージを表示`UserName`"MOORE、BOBBY"では、プロシージャを呼び出す、`Capitalize`オブジェクトのメソッドです。  
  
2.  をクリックして**OK**メッセージ ボックスを閉じます。 `Button1 Click`プロシージャの値を変更する、`UserName`プロパティの新しい値のことを示すメッセージを表示および`UserName`"Worden、Joe"は、します。  
  
## <a name="see-also"></a>関連項目

[オブジェクト指向プログラミング (Visual Basic)](../../concepts/object-oriented-programming.md)  
[クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)