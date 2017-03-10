---
title: "イベント (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "classes [C#], イベント"
  - "C# 言語、イベント"
  - "イベント [C#]"
ms.assetid: a8e51b22-d294-44fb-9539-0072f06c4cb3
caps.latest.revision: 43
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 43
---
# イベント (C# プログラミング ガイド)
[クラス](../../../csharp/language-reference/keywords/class.md)やオブジェクトは、何か重要なことが起こった場合に、イベントを使用して他のクラスまたはオブジェクトに通知を送ります。 イベントを送信する \(*発生させる*\) クラスを*パブリッシャー*、イベントを受信する \(*処理する*\) クラスを*サブスクライバー*と呼びます。  
  
 一般的な C\# Windows フォームまたは Web アプリケーションでは、ボタンやリスト ボックスなどのコントロールによって発生したイベントを定期受信します。[!INCLUDE[csprcs](../../../csharp/includes/csprcs-md.md)] 統合開発環境 \(IDE\) を使用して、コントロールによって発行されるイベントを参照し、処理するイベントを選択できます。 IDE は、空のイベント ハンドラー メソッドとイベントを定期受信するためのコードを自動的に追加します。 詳細については、「[方法 : イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)」を参照してください。  
  
## イベントの概要  
 イベントには次のようなプロパティがあります。  
  
-   パブリッシャーがイベントが発生するタイミングを判断し、サブスクライバーがイベントに対応して実行するアクションを決定します。  
  
-   イベントには複数のサブスクライバーを指定できます。 サブスクライバーは、複数のパブリッシャーからの複数のイベントを処理できます。  
  
-   サブスクライバーがないイベントは発生しません。  
  
-   イベントは一般的に、グラフィカル ユーザー インターフェイスでのボタンのクリックやメニューの選択などのユーザーの操作を知らせるために使用されます。  
  
-   イベントに複数のサブスクライバーがある場合は、イベントが発生したときに複数のイベント ハンドラーが同時に呼び出されます。 イベントを非同期に呼び出すには、「[Calling Synchronous Methods Asynchronously](../Topic/Calling%20Synchronous%20Methods%20Asynchronously.md)」を参照してください。  
  
-   [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] クラス ライブラリ以内で、イベントは、<xref:System.EventHandler> デリゲートおよび <xref:System.EventArgs> 基底クラスを基にしています。  
  
## 関連項目  
 詳細については次を参照してください:  
  
-   [方法 : イベント サブスクリプションとサブスクリプションの解除](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)  
  
-   [方法 : .NET Framework ガイドラインに準拠したイベントを発行する](../../../csharp/programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md)  
  
-   [方法 : 派生クラスから基本クラス イベントを発生させる](../../../csharp/programming-guide/events/how-to-raise-base-class-events-in-derived-classes.md)  
  
-   [方法 : インターフェイス イベントを実装する](../../../csharp/programming-guide/events/how-to-implement-interface-events.md)  
  
-   [スレッドの同期](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)  
  
-   [方法 : ディクショナリを使用してイベント インスタンスを格納する](../../../csharp/programming-guide/events/how-to-use-a-dictionary-to-store-event-instances.md)  
  
-   [方法 : カスタム イベント アクセサーを実装する](../../../csharp/programming-guide/events/how-to-implement-custom-event-accessors.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参考書籍の該当する章  
 『[C\# 3.0 Cookbook, Third Edition: More than 250 solutions for C\# 3.0 programmers \(C\# 3.0 クックブック \(第 3 版\): C\# 3.0 プログラマ向けの 250 以上のソリューション\)](http://go.microsoft.com/fwlink/?LinkId=195369)』の「[Delegates, Events, and Lambda Expressions \(デリゲート、イベント、およびラムダ式\)](http://go.microsoft.com/fwlink/?LinkId=195395)」  
  
 「[Learning C\# 3.0: Master the Fundamentals of C\# 3.0 \(C\# 3.0 の学習: C\# 3.0 の基礎を習得\)](http://go.microsoft.com/fwlink/?LinkId=195412)」の「[Delegates and Events \(デリゲートおよびイベント\)](http://go.microsoft.com/fwlink/?LinkId=195418)」  
  
## 参照  
 <xref:System.EventHandler>   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [デリゲート](../../../csharp/programming-guide/delegates/index.md)   
 [Windows フォーム内でのイベント ハンドラーの作成](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)   
 [Multithreaded Programming with the Event\-based Asynchronous Pattern](../Topic/Multithreaded%20Programming%20with%20the%20Event-based%20Asynchronous%20Pattern.md)