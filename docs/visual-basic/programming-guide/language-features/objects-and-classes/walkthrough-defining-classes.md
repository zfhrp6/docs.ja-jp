---
title: "クラスの定義 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- execution, ending
- objects [Visual Basic], initializing
- Initialize event
- files, closing
- programs, quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event
- execution, stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: aeaa5c2bb85c1a642da15c6a29546cf065380e27
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-defining-classes-visual-basic"></a>チュートリアル: クラスの定義 (Visual Basic)
このチュートリアルでは、オブジェクトの作成に使用することができますし、クラスを定義する方法を示します。 また、新しいクラスにプロパティとメソッドを追加する方法を説明し、オブジェクトを初期化する方法を示します。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-a-class"></a>クラスを定義するには  
  
1.  クリックして、プロジェクトを作成**新しいプロジェクト**上、**ファイル**メニュー。 **[新しいプロジェクト]** ダイアログ ボックスが表示されます。  
  
2.  一覧から Windows アプリケーションを選択[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクト テンプレートを新しいプロジェクトを表示します。  
  
3.  クリックして新しいクラスをプロジェクトに追加**クラスの追加**上、**プロジェクト**メニュー。 **新しい項目の追加** ダイアログ ボックスが表示されます。  
  
4.  選択、**クラス**テンプレートです。  
  
5.  新しいクラスの名前を`UserNameInfo.vb`、 をクリックし、**追加**新しいクラスのコードを表示します。  
  
     [!code-vb[VbVbalrOOP&#5;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  使用することができます、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] **コード エディター** 」と入力してクラスをスタートアップ フォームに追加する、`Class`キーワードの後に、新しいクラスの名前。 **コード エディター** 、対応する説明`End Class`するステートメントです。  
  
6.  間に次のコードを追加することで、クラスのプライベート フィールドを定義、`Class`と`End Class`ステートメント。  
  
     [!code-vb[VbVbalrOOP&#7;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     ものとしてフィールドを宣言する`Private`クラス内でのみ使用できることを意味します。 利用できるフィールドからクラスの外部でなどのアクセス修飾子を使用して、`Public`以上のアクセスを提供します。 詳細については、次を参照してください。 [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)します。  
  
7.  次のコードを追加することで、クラスのプロパティを定義します。  
  
     [!code-vb[VbVbalrOOP&#8;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  次のコードを追加することで、クラスのメソッドを定義します。  
  
     [!code-vb[VbVbalrOOP&#9;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. という名前のプロシージャを追加することで、新しいクラスにパラメーター化されたコンス トラクターを定義`Sub New`:  
  
     [!code-vb[VbVbalrOOP&#10;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     `Sub New`コンス トラクターはこのクラスに基づくオブジェクトの作成時に自動的に呼び出されます。 このコンス トラクターは、ユーザー名を保持するフィールドの値を設定します。  
  
### <a name="to-create-a-button-to-test-the-class"></a>クラスをテストするためのボタンを作成するには  
  
1.  その名前を右クリックして、スタートアップ フォームをデザイン モードに変更**ソリューション エクスプ ローラー**クリックし、**ビュー デザイナー**します。 既定では、Windows アプリケーション プロジェクトのスタートアップ フォームを Form1.vb と呼びます。 メイン フォームが表示されます。  
  
2.  メイン フォームにボタンを追加し、ダブルクリックのコードを表示して、`Button1_Click`イベント ハンドラーです。 テストのプロシージャを呼び出すには、次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP&#12;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a>アプリケーションを実行するには  
  
1.  F5 キーを押して、アプリケーションを実行します。 テスト プロシージャを呼び出すためのフォーム上のボタンをクリックします。 元のことを示すメッセージが表示`UserName`"MOORE、BOBBY"は、プロシージャが呼び出されるため、`Capitalize`オブジェクトのメソッドです。  
  
2.  クリックして**OK**メッセージ ボックスを閉じます。 `Button1 Click`の値を変更する手順、`UserName`プロパティの新しい値のことを示すメッセージを表示および`UserName`"Worden、Joe"は、です。  
  
## <a name="see-also"></a>関連項目  
 [オブジェクト指向プログラミング](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)   
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

