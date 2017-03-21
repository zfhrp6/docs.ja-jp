---
title: "作成するインターフェイスと実装 (Visual Basic) |Microsoft ドキュメント"
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
- interfaces, walkthroughs
- interfaces, testing
- interface implementation, walkthrough
- interfaces, creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 076bc8d33e97286c31f27a2016e39a25e9cec22c
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>チュートリアル: インターフェイスの作成と実装 (Visual Basic)
インターフェイスは、プロパティ、メソッド、およびイベントの特性を記述する、最大で構造体またはクラスの実装の詳細のままです。  
  
 このチュートリアルでは、宣言およびインターフェイスを実装する方法を示します。  
  
> [!NOTE]
>  このチュートリアルでは、ユーザー インターフェイスを作成する方法に関する情報を提供しません。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-define-an-interface"></a>インターフェイスを定義するには  
  
1.  新しい[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]Windows アプリケーション プロジェクト。  
  
2.  クリックして、プロジェクトに新しいモジュールを追加**モジュールの追加**上、**プロジェクト**メニュー。  
  
3.  新しいモジュール名前`Module1.vb` をクリック**追加**します。 新しいモジュールのコードが表示されます。  
  
4.  という名前のインターフェイスを定義する`TestInterface`内`Module1`」と入力して`Interface TestInterface`間、`Module`と`End Module`ステートメント、および ENTER キーを押します。 **コード エディター**インデント、`Interface`キーワードを追加し、`End Interface`コード ブロックを形成するステートメントです。  
  
5.  間に次のコードを配置することで、プロパティ、メソッド、およびインターフェイスのイベントを定義、`Interface`と`End Interface`ステートメント。  
  
     [!code-vb[VbVbalrOOP #&98;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a>実装  
 インターフェイス メンバーの宣言に使用する構文はクラス メンバーを宣言するための構文を異なることに注意してください可能性があります。 この違いは、インターフェイスが実装コードを含めることはできませんという事実を表しています。  
  
#### <a name="to-implement-the-interface"></a>インターフェイスを実装するには  
  
1.  という名前のクラスを追加`ImplementationClass`に次のステートメントを追加することで`Module1`後に、`End Interface`ステートメント前に、`End Module`ステートメント、および ENTER キーを押します。  
  
     [!code-vb[VbVbalrOOP&#99;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     統合開発環境で作業している場合、**コード エディター**提供、対応する`End Class`ステートメント ENTER キーを押す。  
  
2.  次の追加`Implements`ステートメント`ImplementationClass`を実装するクラス、インターフェイスを示しています。  
  
     [!code-vb[VbVbalrOOP&#100;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     クラスまたは構造の上部にある他の項目とは別に表示されている場合、`Implements`ステートメントでは、クラスまたは構造体でインターフェイスを実装することを示します。  
  
     統合開発環境で作業している場合、**コード エディター**で必要なクラス メンバーを実装して`TestInterface`、ENTER キーを押すし、次の手順をスキップすることができます。  
  
3.  統合開発環境で機能しない場合は、インターフェイスのすべてのメンバーを実装する必要があります`MyInterface`します。 次のコードを追加`ImplementationClass`を実装する`Event1`、 `Method1`、および`Prop1`:  
  
     [!code-vb[VbVbalrOOP #&101;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     `Implements`ステートメント インターフェイスおよび実装するインターフェイス メンバーの名前します。  
  
4.  定義が完了`Prop1`プロパティ値を格納するクラスにプライベート フィールドを追加します。  
  
     [!code-vb[VbVbalrOOP #&102;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     値を返す、`pval`プロパティ アクセサーを取得します。  
  
     [!code-vb[VbVbalrOOP #&103;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     値を設定`pval`プロパティのアクセサーを設定します。  
  
     [!code-vb[VbVbalrOOP #&104;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  定義が完了`Method1`によって次のコードを追加します。  
  
     [!code-vb[VbVbalrOOP #&105;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a>インターフェイスの実装をテストするには  
  
1.  プロジェクトのスタートアップ フォームを右クリックし、**ソリューション エクスプ ローラー**、 をクリック**コードの表示**します。 エディターには、スタートアップ フォームのクラスが表示されます。 既定では、スタートアップ フォームと呼ばれる`Form1`です。  
  
2.  次の追加`testInstance`フィールドを`Form1`クラス。  
  
     [!code-vb[VbVbalrOOP #&120;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     宣言することで`testInstance`として`WithEvents`、`Form1`クラスは、そのイベントを処理できます。  
  
3.  次のイベント ハンドラーを追加、`Form1`クラスによって生成されるイベントを処理する`testInstance`:  
  
     [!code-vb[VbVbalrOOP #&106;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  という名前のサブルーチンを追加`Test`に、`Form1`実装クラスをテストするクラス。  
  
     [!code-vb[VbVbalrOOP #&107;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     `Test`プロシージャを実装するクラスのインスタンスの作成`MyInterface`、そのインスタンスを割り当てる、`testInstance`フィールド、プロパティの設定およびインターフェイスを通じたメソッドを実行します。  
  
5.  呼び出すコードを追加、`Test`プロシージャから、`Form1 Load`スタートアップ フォームの手順。  
  
     [!code-vb[VbVbalrOOP #&108;](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  実行、 `Test` f5 キーを押してプロシージャです。 メッセージ「Prop1 に設定されて 9」が表示されます。 クリックした後、メッセージ「Method1 の X パラメーターが 5」が表示されます。 [Ok] をクリックし、「イベント ハンドラーは、イベントをキャッチ」メッセージが表示されます。  
  
## <a name="see-also"></a>関連項目  
 [Implements ステートメント](../../../../visual-basic/language-reference/statements/implements-statement.md)   
 [インターフェイス](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)   
 [Interface ステートメント](../../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Event ステートメント](../../../../visual-basic/language-reference/statements/event-statement.md)

