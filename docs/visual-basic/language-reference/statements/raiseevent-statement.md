---
title: "RaiseEvent ステートメント |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
dev_langs:
- VB
helpviewer_keywords:
- raising events, RaiseEvent statement
- RaiseEvent statement
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: 19
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
ms.openlocfilehash: 059b1347c4a35b896f5aa19cadb28fbceb8b25c9
ms.lasthandoff: 03/13/2017

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
 省略可能です。 変数、配列、または式のコンマ区切りリスト。 `argumentlist`引数をかっこで囲む必要があります。 引数がない場合は、かっこを省略する必要があります。  
  
## <a name="remarks"></a>コメント  
 必要な`eventname`は、モジュール内で宣言されたイベントの名前。 これは、Visual Basic 変数の名前付け規則に従います。  
  
 イベントは発生のモジュール内で宣言されていない、エラーが発生します。 次のコード フラグメントでは、イベントの宣言と、イベントが発生する手順を示しています。  
  
 [!code-vb[VbVbalrEvents #&37;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 使用することはできません`RaiseEvent`モジュールで明示的に宣言されていないイベントを発生させます。 たとえば、すべてのフォームの継承、<xref:System.Windows.Forms.Control.Click>からイベントを<xref:System.Windows.Forms.Form?displayProperty=fullName>を使用すると発生することはできません`RaiseEvent`派生フォームで</xref:System.Windows.Forms.Form?displayProperty=fullName></xref:System.Windows.Forms.Control.Click>。 宣言する場合、`Click`イベント モジュールでは、フォーム、フォーム自体のシャドウ<xref:System.Windows.Forms.Control.Click>イベント</xref:System.Windows.Forms.Control.Click>。 フォームを引き続き呼び出すことができます<xref:System.Windows.Forms.Control.Click>イベントを呼び出して、<xref:System.Windows.Forms.Control.OnClick%2A>メソッド</xref:System.Windows.Forms.Control.OnClick%2A></xref:System.Windows.Forms.Control.Click>。  
  
 既定では、Visual Basic で定義されたイベントは、接続が確立されている順序では、そのイベント ハンドラーを生成します。 イベントがあるため`ByRef`パラメーター、接続するプロセスは以前のイベント ハンドラーによって変更されているパラメーターを受け取ることがあります。 イベント ハンドラーの実行後は、イベントを発生させたサブルーチンに制御が返されます。  
  
> [!NOTE]
>  非共有イベントが宣言されているクラスのコンス トラクター内で発生しない必要があります。 このようなイベントでは、実行時エラーが発生しない、関連付けられたイベント ハンドラーでキャッチできる、されない場合があります。 使用して、`Shared`修飾子をコンス トラクターからイベントを発生させる必要がある場合は、共有のイベントを作成します。  
  
> [!NOTE]
>  イベントの既定の動作を変更するには、カスタム イベントを定義します。 カスタム イベントの場合、`RaiseEvent`ステートメントで呼び出されるイベントの`RaiseEvent`アクセサー。 カスタム イベントの詳細については、次を参照してください。 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)します。  
  
## <a name="example"></a>例  
 次の例では、イベントを使用して 10 秒から 0 秒までカウント ダウンします。 コードに示すいくつかのイベントに関連するメソッド、プロパティ、およびなど、ステートメント、`RaiseEvent`ステートメントです。  
  
 イベントを発生させるクラスをイベント ソース、イベントを処理するメソッドをイベント ハンドラーと呼びます。 イベント ソースでは、生成されるイベントに対して複数のイベント ハンドラーを設定できます。 クラスでイベントが発生すると、そのイベントは、オブジェクトのインスタンスに対するイベントを処理するために選択されたすべてのクラスで発生します。  
  
 また、この例では、ボタン (`Button1`) とテキスト ボックス (`TextBox1`) を含んだフォーム (`Form1`) も使用しています。 ボタンをクリックすると、1 つ目のテキスト ボックスに 10 秒から 0 秒までのカウントダウンが表示されます。 カウントダウンが終わると (10 秒が経過すると)、1 つ目のテキスト ボックスに "Done" と表示されます。  
  
 `Form1` のコードでは、フォームの初期状態と終了状態を指定しています。 イベント発生時に実行されるコードも含まれています。  
  
 この例を使用する新しい Windows アプリケーション プロジェクトを開き、という名前のボタンを追加`Button1`とという名前のテキスト ボックス`TextBox1`という名前のメイン フォームに`Form1`します。 フォームを右クリックし、をクリックし、**コードの表示**コード エディターを開きます。  
  
 追加、`WithEvents`変数の宣言セクションに、`Form1`クラスです。  
  
 [!code-vb[VbVbalrEvents&#14;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a>例  
 `Form1` のコードに次のコードを追加します。 など、存在するすべての重複するプロシージャを置き換える`Form_Load`、または`Button_Click`です。  
  
 [!code-vb[VbVbalrEvents&#15;](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 前の例を実行 ボタンをクリックして f5 キーを押して**開始**します。 最初のテキスト ボックスで、秒のカウント ダウンが開始されます。 カウントダウンが終わると (10 秒が経過すると)、1 つ目のテキスト ボックスに "Done" と表示されます。  
  
> [!NOTE]
>  `My.Application.DoEvents`フォームは、メソッドがまったく同じ方法でイベントを処理できません。 使用できるイベントを直接処理するためのフォームを許可するようにマルチ スレッドです。 詳細については、次を参照してください。[スレッド](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)します。  
  
## <a name="see-also"></a>関連項目  
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)   
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)   
 [AddHandler ステートメント](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [RemoveHandler ステートメント](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [ハンドル](../../../visual-basic/language-reference/statements/handles-clause.md)
