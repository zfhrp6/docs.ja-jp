---
title: 作成と実装インターフェイス (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: af9305deb60637b642d091501e743f2c7a57ccad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>チュートリアル: インターフェイスの作成と実装 (Visual Basic)

インターフェイスは、プロパティ、メソッド、およびイベントの特性を記述が最大構造体またはクラスの実装の詳細のままにします。  
  
 このチュートリアルでは、宣言およびインターフェイスを実装する方法を示します。  
  
> [!NOTE]
>  このチュートリアルでは、ユーザー インターフェイスを作成する方法に関する情報を提供しません。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>インターフェイスを定義するには
  
1.  新しい Visual Basic Windows アプリケーション プロジェクトを開きます。  
  
2.  クリックして、プロジェクトに新しいモジュールを追加**モジュールの追加**上、**プロジェクト**メニュー。  
  
3.  新しいモジュールの名前を付けます`Module1.vb` をクリック**追加**です。 新しいモジュールのコードが表示されます。  
  
4.  という名前のインターフェイスを定義する`TestInterface`内`Module1`」と入力して`Interface TestInterface`間、`Module`と`End Module`ステートメント、および ENTER キーを押します。 **コード エディター**インデント、`Interface`キーワードを追加し、`End Interface`コード ブロックを形成するステートメント。  
  
5.  間に次のコードを配置することで、プロパティ、メソッド、およびインターフェイスのイベントを定義、`Interface`と`End Interface`ステートメント。  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>実装

 インターフェイス メンバーを宣言するために使用する構文はクラス メンバーを宣言するための構文を異なることに注意してください可能性があります。 この違いは、インターフェイスが実装コードを含むことができないという事実を反映します。  
  
### <a name="to-implement-the-interface"></a>インターフェイスを実装するには
  
1.  という名前のクラスを追加`ImplementationClass`に次のステートメントを追加することによって`Module1`の後に、`End Interface`ステートメント前に、`End Module`ステートメント、および ENTER キーを押します。  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     統合開発環境で作業している場合、**コード エディター**に対応する提供`End Class`ステートメント ENTER キーを押す。  
  
2.  次の追加`Implements`ステートメントを`ImplementationClass`、名前、インターフェイス、クラスを実装します。  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     クラスまたは構造の上部にある他の項目とは別に表示されている場合、`Implements`ステートメントでは、クラスまたは構造体がインターフェイスを実装することを示します。  
  
     統合開発環境で作業している場合、**コード エディター**で必要なクラス メンバーを実装して`TestInterface`、ENTER キーを押すし、次の手順をスキップすることができます。  
  
3.  統合開発環境で作業していない場合は、インターフェイスのすべてのメンバーを実装する必要があります`MyInterface`です。 次のコードを追加`ImplementationClass`を実装する`Event1`、 `Method1`、および`Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements`ステートメント インターフェイスおよび実装するインターフェイス メンバーの名前します。  
  
4.  定義を完了`Prop1`プロパティ値を格納するクラスにプライベート フィールドを追加することで。  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     値を返す、`pval`プロパティ アクセサーを取得します。  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     値を設定`pval`プロパティでアクセサーを設定します。  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5.  定義を完了`Method1`次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>インターフェイスの実装をテストするには
  
1.  プロジェクトをスタートアップ フォームを右クリックし、**ソリューション エクスプ ローラー**、 をクリック**コードの表示**です。 エディターには、スタートアップ フォームのクラスが表示されます。 既定では、スタートアップ フォームと呼ばれる`Form1`です。  
  
2.  次の追加`testInstance`フィールドを`Form1`クラス。  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     宣言することによって`testInstance`として`WithEvents`、`Form1`クラスは、そのイベントを処理できます。  
  
3.  次のイベント ハンドラーを追加、`Form1`クラスによって生成されるイベントを処理する`testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4.  という名前のサブルーチンを追加`Test`を`Form1`実装クラスをテストするクラス。  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test`プロシージャを実装するクラスのインスタンスの作成`MyInterface`、そのインスタンスに割り当てます、`testInstance`フィールド、プロパティの設定し、インターフェイス メソッドを実行します。  
  
5.  呼び出すコードを追加、`Test`プロシージャから、`Form1 Load`スタートアップ フォームの手順。  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6.  実行、 `Test` f5 キーを押してプロシージャです。 メッセージ「Prop1 に設定された 9」が表示されます。 クリックした後、メッセージ"Method1 の X パラメーターは、5 を is"が表示されます。 [Ok]、をクリックし、「イベント ハンドラーが、イベントが発生しました」メッセージが表示されます。  
  
## <a name="see-also"></a>関連項目

 [Implements ステートメント](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [インターフェイス](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Interface ステートメント](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)  