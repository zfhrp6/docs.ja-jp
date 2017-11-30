---
title: "作成と実装インターフェイス (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08bf6dc7344d4f83c8ab1908fdeb29eb4a53e142
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>チュートリアル: インターフェイスの作成と実装 (Visual Basic)
インターフェイスは、プロパティ、メソッド、およびイベントの特性を記述が最大構造体またはクラスの実装の詳細のままにします。  
  
 このチュートリアルでは、宣言およびインターフェイスを実装する方法を示します。  
  
> [!NOTE]
>  このチュートリアルでは、ユーザー インターフェイスを作成する方法に関する情報を提供しません。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-an-interface"></a>インターフェイスを定義するには  
  
1.  新しい [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Windows アプリケーション プロジェクトを開きます。  
  
2.  クリックして、プロジェクトに新しいモジュールを追加**モジュールの追加**上、**プロジェクト**メニュー。  
  
3.  新しいモジュールの名前を付けます`Module1.vb` をクリック**追加**です。 新しいモジュールのコードが表示されます。  
  
4.  という名前のインターフェイスを定義する`TestInterface`内`Module1`」と入力して`Interface TestInterface`間、`Module`と`End Module`ステートメント、および ENTER キーを押します。 **コード エディター**インデント、`Interface`キーワードを追加し、`End Interface`コード ブロックを形成するステートメント。  
  
5.  間に次のコードを配置することで、プロパティ、メソッド、およびインターフェイスのイベントを定義、`Interface`と`End Interface`ステートメント。  
  
     [!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a>実装  
 インターフェイス メンバーを宣言するために使用する構文はクラス メンバーを宣言するための構文を異なることに注意してください可能性があります。 この違いは、インターフェイスが実装コードを含むことができないという事実を反映します。  
  
#### <a name="to-implement-the-interface"></a>インターフェイスを実装するには  
  
1.  という名前のクラスを追加`ImplementationClass`に次のステートメントを追加することによって`Module1`の後に、`End Interface`ステートメント前に、`End Module`ステートメント、および ENTER キーを押します。  
  
     [!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     統合開発環境で作業している場合、**コード エディター**に対応する提供`End Class`ステートメント ENTER キーを押す。  
  
2.  次の追加`Implements`ステートメントを`ImplementationClass`、名前、インターフェイス、クラスを実装します。  
  
     [!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     クラスまたは構造の上部にある他の項目とは別に表示されている場合、`Implements`ステートメントでは、クラスまたは構造体がインターフェイスを実装することを示します。  
  
     統合開発環境で作業している場合、**コード エディター**で必要なクラス メンバーを実装して`TestInterface`、ENTER キーを押すし、次の手順をスキップすることができます。  
  
3.  統合開発環境で作業していない場合は、インターフェイスのすべてのメンバーを実装する必要があります`MyInterface`です。 次のコードを追加`ImplementationClass`を実装する`Event1`、 `Method1`、および`Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     `Implements`ステートメント インターフェイスおよび実装するインターフェイス メンバーの名前します。  
  
4.  定義を完了`Prop1`プロパティ値を格納するクラスにプライベート フィールドを追加することで。  
  
     [!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     値を返す、`pval`プロパティ アクセサーを取得します。  
  
     [!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     値を設定`pval`プロパティでアクセサーを設定します。  
  
     [!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  定義を完了`Method1`次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a>インターフェイスの実装をテストするには  
  
1.  プロジェクトをスタートアップ フォームを右クリックし、**ソリューション エクスプ ローラー**、 をクリック**コードの表示**です。 エディターには、スタートアップ フォームのクラスが表示されます。 既定では、スタートアップ フォームと呼ばれる`Form1`です。  
  
2.  次の追加`testInstance`フィールドを`Form1`クラス。  
  
     [!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     宣言することによって`testInstance`として`WithEvents`、`Form1`クラスは、そのイベントを処理できます。  
  
3.  次のイベント ハンドラーを追加、`Form1`クラスによって生成されるイベントを処理する`testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  という名前のサブルーチンを追加`Test`を`Form1`実装クラスをテストするクラス。  
  
     [!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     `Test`プロシージャを実装するクラスのインスタンスの作成`MyInterface`、そのインスタンスに割り当てます、`testInstance`フィールド、プロパティの設定し、インターフェイス メソッドを実行します。  
  
5.  呼び出すコードを追加、`Test`プロシージャから、`Form1 Load`スタートアップ フォームの手順。  
  
     [!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  実行、 `Test` f5 キーを押してプロシージャです。 メッセージ「Prop1 に設定された 9」が表示されます。 クリックした後、メッセージ"Method1 の X パラメーターは、5 を is"が表示されます。 [Ok]、をクリックし、「イベント ハンドラーが、イベントが発生しました」メッセージが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [Implements ステートメント](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [インターフェイス](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Interface ステートメント](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)
