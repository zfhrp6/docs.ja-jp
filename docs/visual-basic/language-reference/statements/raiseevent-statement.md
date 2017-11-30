---
title: "RaiseEvent ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2575598577820bd7a72fae2d9b8ba52978f5952d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="raiseevent-statement"></a>RaiseEvent ステートメント
クラス、フォーム、またはドキュメント内のモジュール レベルで宣言されているイベントをトリガーします。  
  
## <a name="syntax"></a>構文  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>指定項目  
 `eventname`  
 必須です。 トリガーするイベントの名前です。  
  
 `argumentlist`  
 省略可能です。 変数、配列、または式のコンマ区切り一覧。 `argumentlist`引数はかっこで囲む必要があります。 引数がない場合は、かっこを省略する必要があります。  
  
## <a name="remarks"></a>コメント  
 必要な`eventname`は、モジュール内で宣言されたイベントの名前。 Visual Basic 変数の名前付け規則に従うことです。  
  
 イベントが生成されるモジュール内で宣言されていない、エラーが発生します。 次のコード フラグメントは、イベントの宣言とイベントが発生する手順を示します。  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 使用することはできません`RaiseEvent`モジュールで明示的に宣言されていないイベントを発生させます。 たとえば、すべてのフォームの継承、<xref:System.Windows.Forms.Control.Click>からイベント<xref:System.Windows.Forms.Form?displayProperty=nameWithType>を使用すると発生することはできません`RaiseEvent`派生フォームでします。 宣言する場合、`Click`イベント モジュールでは、フォーム、フォーム自体のシャドウ<xref:System.Windows.Forms.Control.Click>イベント。 フォームを呼び出すことができますも<xref:System.Windows.Forms.Control.Click>を呼び出してイベント、<xref:System.Windows.Forms.Control.OnClick%2A>メソッドです。  
  
 既定では、Visual Basic で定義されたイベントは、接続が確立されている順序では、そのイベント ハンドラーを生成します。 イベントがあるため`ByRef`パラメーター、接続するプロセスは、以前のイベント ハンドラーによって変更されているパラメーターを受け取る可能性があります。 イベント ハンドラーの実行後にイベントを発生させたサブルーチンに制御が返されます。  
  
> [!NOTE]
>  非共有イベントが宣言されているクラスのコンス トラクター内で発生しない必要があります。 このようなイベントでは、実行時エラーが発生しない、関連付けられたイベント ハンドラーによってキャッチするされない場合があります。 使用して、`Shared`修飾子をコンス トラクターからイベントを発生させる必要がある場合は、共有のイベントを作成します。  
  
> [!NOTE]
>  イベントの既定の動作を変更するには、カスタム イベントを定義します。 カスタム イベントの場合、`RaiseEvent`ステートメントには、イベントが呼び出される`RaiseEvent`アクセサー。 カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)です。  
  
## <a name="example"></a>例  
 次の例では、イベントを使用して 10 秒から 0 秒までカウント ダウンします。 イベントに関連するメソッド、プロパティ、およびなど、ステートメントのいくつかのコードに示す、`RaiseEvent`ステートメントです。  
  
 イベントを発生させるクラスをイベント ソース、イベントを処理するメソッドをイベント ハンドラーと呼びます。 イベント ソースでは、生成されるイベントに対して複数のイベント ハンドラーを設定できます。 クラスでイベントが発生すると、そのイベントは、オブジェクトのインスタンスに対するイベントを処理するために選択されたすべてのクラスで発生します。  
  
 また、この例では、ボタン (`Button1`) とテキスト ボックス (`TextBox1`) を含んだフォーム (`Form1`) も使用しています。 ボタンをクリックすると、1 つ目のテキスト ボックスに 10 秒から 0 秒までのカウントダウンが表示されます。 カウントダウンが終わると (10 秒が経過すると)、1 つ目のテキスト ボックスに "Done" と表示されます。  
  
 `Form1` のコードでは、フォームの初期状態と終了状態を指定しています。 イベント発生時に実行されるコードも含まれています。  
  
 この例を使用する新しい Windows アプリケーション プロジェクトを開き、という名前のボタンの追加`Button1`という名前のテキスト ボックスおよび`TextBox1`という名前のメイン フォームに`Form1`です。 フォームを右クリックし、をクリックし、**コードの表示**コード エディターを開きます。  
  
 追加、`WithEvents`変数の宣言セクションに、`Form1`クラスです。  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a>例  
 `Form1` のコードに次のコードを追加します。 など、存在するすべての重複するプロシージャを置き換える`Form_Load`、または`Button_Click`です。  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 前の例を実行し、ボタンをクリックして f5 キーを押して**開始**です。 最初のテキスト ボックスで、秒のカウント ダウンが開始されます。 カウントダウンが終わると (10 秒が経過すると)、1 つ目のテキスト ボックスに "Done" と表示されます。  
  
> [!NOTE]
>  `My.Application.DoEvents`の形式として、メソッドがまったく同じ方法でイベントを処理できません。 使用することができますを許可するフォームがイベントを直接処理する場合のマルチ スレッド化します。 詳細については、次を参照してください。[スレッド](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)です。  
  
## <a name="see-also"></a>関連項目  
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
 [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
