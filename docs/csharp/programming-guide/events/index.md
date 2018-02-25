---
title: "イベント (C# プログラミング ガイド)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- classes [C#], events
- C# language, events
- events [C#]
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 72563b9e37c26257a2bf5939f63ece050ec003ab
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/24/2018
---
# <a name="events-c-programming-guide"></a>イベント (C# プログラミング ガイド)
[クラス](../../../csharp/language-reference/keywords/class.md) やオブジェクトは、何か重要なことが起こった場合に、イベントを使用して他のクラスまたはオブジェクトに通知を送ります。 イベントを送信する ( *発生させる*) クラスを *パブリッシャー* 、イベントを受信する ( *処理する*) クラスを *サブスクライバー*と呼びます。  
  
 一般的な C# Windows フォームまたは Web アプリケーションでは、ボタンやリスト ボックスなどのコントロールによって発生したイベントを定期受信します。 [!INCLUDE[csprcs](~/includes/csprcs-md.md)] 統合開発環境 (IDE) を使用して、コントロールによって発行されるイベントを参照し、処理するイベントを選択できます。 IDE は、空のイベント ハンドラー メソッドとイベントを定期受信するためのコードを自動的に追加します。 詳細については、「[方法: イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。  
  
## <a name="events-overview"></a>イベントの概要  
 イベントには次のようなプロパティがあります。  
  
-   パブリッシャーがイベントが発生するタイミングを判断し、サブスクライバーがイベントに対応して実行するアクションを決定します。  
  
-   イベントには複数のサブスクライバーを指定できます。 サブスクライバーは、複数のパブリッシャーからの複数のイベントを処理できます。  
  
-   サブスクライバーがないイベントは発生しません。  
  
-   イベントは一般的に、グラフィカル ユーザー インターフェイスでのボタンのクリックやメニューの選択などのユーザーの操作を知らせるために使用されます。  
  
-   イベントに複数のサブスクライバーがある場合は、イベントが発生したときに複数のイベント ハンドラーが同時に呼び出されます。 イベントを非同期に呼び出すには、「 [Calling Synchronous Methods Asynchronously](../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)」を参照してください。  
  
-   [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] クラス ライブラリ以内で、イベントは、 <xref:System.EventHandler> デリゲートおよび <xref:System.EventArgs> 基底クラスを基にしています。  
  
## <a name="related-sections"></a>関連項目  
 詳細については次を参照してください:  
  
-   [方法: イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [方法: .NET Framework ガイドラインに準拠したイベントを発行する](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [方法: 派生クラスから基本クラス イベントを発生させる](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [方法: インターフェイス イベントを実装する](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [スレッドの同期](../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)  
  
-   [方法: ディクショナリを使用してイベント インスタンスを格納する](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [方法: カスタム イベント アクセサーを実装する](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## <a name="c-language-specification"></a>C# 言語仕様  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="featured-book-chapters"></a>参考書籍の該当する章  
 『 [Delegates, Events, and Lambda Expressions (デリゲート、イベント、およびラムダ式) (C# 3.0 クックブック (第 3 版): C# 3.0 プログラマ向けの 250 以上のソリューション)](https://msdn.microsoft.com/library/orm-9780596516109-03-09.aspx) 』の「 [Delegates, Events, and Lambda Expressions (デリゲート、イベント、およびラムダ式)](https://msdn.microsoft.com/library/orm-9780596516109-03.aspx) 」  
  
 「[Learn」の「g C# 3.0: Master the Fundamentals of C# 3.0 (C# 3.0 の学習: C# 3.0 の基礎を習得)](https://msdn.microsoft.com/library/orm-9780596521066-01-17.aspx) 」の「 [Learn」の「g C# 3.0: Master the fundamentals of C# 3.0](https://msdn.microsoft.com/library/orm-9780596521066-01.aspx)」  
  
## <a name="see-also"></a>参照  
 <xref:System.EventHandler>  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)  
 [Windows フォーム内でのイベント ハンドラーの作成](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [イベント ベースの非同期パターンを使用したマルチスレッド プログラミング](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)
