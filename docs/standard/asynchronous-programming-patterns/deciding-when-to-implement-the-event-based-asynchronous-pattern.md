---
title: "Deciding When to Implement the Event-based Asynchronous Pattern | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Event-based Asynchronous Pattern"
  - "ProgressChangedEventArgs class"
  - "BackgroundWorker component"
  - "events [.NET Framework], asynchronous"
  - "AsyncOperationManager class"
  - "threading [.NET Framework], asynchronous features"
  - "AsyncOperation class"
  - "AsyncCompletedEventArgs class"
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Deciding When to Implement the Event-based Asynchronous Pattern
イベント ベースの非同期パターンは、クラスの非同期動作を公開するためのパターンを提供します。  このパターンを導入すると、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] は、非同期動作を公開するための 2 つのパターンを定義します。<xref:System.IAsyncResult?displayProperty=fullName> インターフェイスに基づく非同期パターンと、イベントベースのパターンです。  このトピックでは、どのような場合にこの 2 つのパターンを実装すればよいかについて説明します。  
  
 <xref:System.IAsyncResult> インターフェイスを使用した非同期プログラミングの詳細については、「[Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)」を参照してください。  
  
## 一般原則  
 一般に、できる限りイベントベースの非同期パターンを使用して非同期機能を公開する必要があります。  ただし、イベント ベースのパターンでは満たすことのできない要件もあります。  その場合は、イベントベースのパターンだけでなく、<xref:System.IAsyncResult> パターンも実装することが必要になることがあります。  
  
> [!NOTE]
>  イベントベースのパターンを実装せずに、<xref:System.IAsyncResult> パターンだけを実装することはまれです。  
  
## ガイドライン  
 イベント ベースの非同期パターンを実装する必要のある場合についてのガイドラインを次に示します。  
  
-   イベントベースのパターンを既定の API として使用して、クラスの非同期動作を公開します。  
  
-   クラスを Windows フォームなどのクライアント アプリケーションで主に使用する場合は、<xref:System.IAsyncResult> パターンを公開しないでください。  
  
-   要件を満たす必要がある場合にだけ、<xref:System.IAsyncResult> パターンを公開します。  たとえば、既存の API との互換性を保つために、<xref:System.IAsyncResult> パターンを公開することが必要な場合があります。  
  
-   イベントベースのパターンを公開せずに、<xref:System.IAsyncResult> パターンだけを公開しないでください。  
  
-   <xref:System.IAsyncResult> パターンを公開する必要がある場合は、高度なオプションとして公開します。  たとえば、プロキシ オブジェクトを生成する場合、<xref:System.IAsyncResult> パターンを生成するオプションと共に、既定でイベントベースのパターンを生成します。  
  
-   <xref:System.IAsyncResult> パターンの実装でイベントベースのパターンの実装を構築します。  
  
-   同じクラスでイベントベースのパターンと <xref:System.IAsyncResult> パターンの両方を公開しないようにしてください。  イベントベースのパターンは "高レベル" のクラスで公開し、<xref:System.IAsyncResult> パターンは "低レベル" のクラスで公開します。  たとえば、<xref:System.Net.WebClient> コンポーネントのイベントベースのパターンを、<xref:System.Web.HttpRequest> クラスの <xref:System.IAsyncResult> パターンと比較します。  
  
    -   互換性を保つために必要な場合は、イベントベースのパターンと <xref:System.IAsyncResult> パターンを同じクラスで公開します。  たとえば、<xref:System.IAsyncResult> パターンを使用する API を既にリリースしている場合、下位互換性を保つために <xref:System.IAsyncResult> パターンを保持する必要があります。  
  
    -   実装を分離すると結果的にオブジェクト モデルが複雑になり、複雑さが実装を分離する利点を上回る場合は、イベントベースのパターンと <xref:System.IAsyncResult> パターンを同じクラスで公開します。  イベントベースのパターンの公開を避けるよりも、単一のクラスで両方のパターンを公開する方が適切です。  
  
    -   イベントベースのパターンと <xref:System.IAsyncResult> パターンを単一のクラスで公開する必要がある場合、<xref:System.ComponentModel.EditorBrowsableState> に設定した <xref:System.ComponentModel.EditorBrowsableAttribute> を使用して、<xref:System.IAsyncResult> パターンの実装を高度な機能としてマークします。  これは、<xref:System.IAsyncResult> のプロパティやメソッドを表示するためではなく、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] の IntelliSense などのデザイン環境に対して示します。  これらのプロパティやメソッドも完全に使用できますが、IntelliSense を使用する開発者には API のより明瞭なビューが用意されています。  
  
## イベントベースのパターンに加え IAsyncResult パターンを公開する際の判断基準  
 前述のシナリオに基づくイベント ベースの非同期パターンには多数の利点がありますが、欠点もいくつかあります。パフォーマンスが最も重要な要件である場合は、これらの欠点を認識しておく必要があります。  
  
 イベントベースのパターンが <xref:System.IAsyncResult> パターンと同様には対処できない 3 つのシナリオは次のとおりです。  
  
-   1 つの <xref:System.IAsyncResult> での待機のブロッキング  
  
-   多数の <xref:System.IAsyncResult> オブジェクトでの待機のブロッキング  
  
-   <xref:System.IAsyncResult> での完了のポーリング  
  
 イベントベースのパターンを使用してこれらのシナリオに対処できますが、<xref:System.IAsyncResult> パターンを使用するよりも煩雑になります。  
  
 多くの場合、開発者は一般的に高いパフォーマンス要件のサービスに対して <xref:System.IAsyncResult> パターンを使用します。  たとえば、完了のシナリオのポーリングは、高パフォーマンスのサーバーの技法です。  
  
 さらに、イベントベースのパターンは、作成するオブジェクト \(特に <xref:System.EventArgs>\) の数が多く、スレッド全体にわたって同期するため、<xref:System.IAsyncResult> パターンに比べ効率が下がります。  
  
 <xref:System.IAsyncResult> パターンを使用する場合に従う推奨事項を次に示します。  
  
-   <xref:System.Threading.WaitHandle> オブジェクトまたは <xref:System.IAsyncResult> オブジェクトのサポートが特に必要な場合にだけ、<xref:System.IAsyncResult> パターンを公開します。  
  
-   <xref:System.IAsyncResult> パターンを使用する既存の API がある場合にだけ、<xref:System.IAsyncResult> パターンを公開します。  
  
-   <xref:System.IAsyncResult> パターンに基づく既存の API がある場合は、次回のリリースでイベントベースのパターンも公開するよう考慮します。  
  
-   検証済みの高いパフォーマンス要件をイベントベースのパターンでは満たすことができず、<xref:System.IAsyncResult> パターンであれば満たすことができる場合にだけ、<xref:System.IAsyncResult> パターンを公開します。  
  
## 参照  
 [Walkthrough: Implementing a Component That Supports the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)   
 [Event\-based Asynchronous Pattern \(EAP\)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)   
 [Multithreaded Programming with the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)   
 [Implementing the Event\-based Asynchronous Pattern](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)   
 [イベントベースの非同期パターンを実装するための推奨される手順](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)   
 [Event\-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)