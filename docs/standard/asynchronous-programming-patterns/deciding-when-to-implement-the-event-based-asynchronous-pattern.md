---
title: "イベントベースの非同期パターンをいつ実装するかの決定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: a00046aa-785d-4f7f-a8e5-d06475ea50da
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 48de1b736c251a61a2ad34975c77bc2bca139626
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="deciding-when-to-implement-the-event-based-asynchronous-pattern"></a>イベントベースの非同期パターンをいつ実装するかの決定
イベント ベースの非同期パターンは、クラスの非同期動作を公開するため、パターンを提供します。 このパターンの導入に伴い、[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]非同期動作を公開するための 2 つのパターンを定義します: 非同期パターンがに基づいて、<xref:System.IAsyncResult?displayProperty=nameWithType>インターフェイス、およびイベント ベースのパターン。 このトピックが両方のパターンを実装するための適切な場合について説明します。  
  
 使用した非同期プログラミングの詳細については、<xref:System.IAsyncResult>インターフェイスを参照してください[イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)です。  
  
## <a name="general-principles"></a>一般原則  
 一般に、- イベント ベースの非同期パターンが使用可能な限り非同期機能を公開する必要があります。 ただし、いくつかの要件を満たしていないイベント ベースのパターンがあります。 その場合を実装する必要があります、<xref:System.IAsyncResult>イベント ベースのパターンに加えてパターン。  
  
> [!NOTE]
>  これはまれであるため、<xref:System.IAsyncResult>も実装されているイベントに基づくパターンせずに実装するパターン。  
  
## <a name="guidelines"></a>ガイドライン  
 次に、イベント ベースの非同期パターンを実装する場合のガイドラインを説明します。  
  
-   既定 API とイベント ベースのパターンを使用して、クラスの非同期動作を公開します。  
  
-   公開しない、<xref:System.IAsyncResult>パターンをクラスは、主に、クライアント アプリケーションで Windows フォームなどの使用時にします。  
  
-   だけを公開、<xref:System.IAsyncResult>パターンを要件を満たすために必要な場合です。 たとえば、既存の API との互換性が必要がありますを公開する、<xref:System.IAsyncResult>パターン。  
  
-   公開しない、<xref:System.IAsyncResult>イベント ベースのパターンを公開せずパターン。  
  
-   必要がありますを公開する場合、<xref:System.IAsyncResult>パターンは、高度なオプションとして。 たとえば、プロキシ オブジェクトを生成する場合、このイベント ベースのパターンを既定では、生成するオプションが生成、<xref:System.IAsyncResult>パターン。  
  
-   イベント ベースのパターンの実装の構築、<xref:System.IAsyncResult>パターンの実装です。  
  
-   両方のイベント ベースのパターンを公開しないように、<xref:System.IAsyncResult>パターンは、同じクラスです。 「高レベル」のクラスでイベント ベースのパターンを公開し、<xref:System.IAsyncResult>パターンの「レベルを下げる」クラスです。 たとえば、イベント ベースのパターンと比較、<xref:System.Net.WebClient>コンポーネントを<xref:System.IAsyncResult>のパターン、<xref:System.Web.HttpRequest>クラスです。  
  
    -   イベント ベースのパターンを公開し、<xref:System.IAsyncResult>パターンは、互換性が必要とするときに、同じクラスです。 たとえばを使用する API が既に解放されている場合、<xref:System.IAsyncResult>パターンでは、保持する必要は、<xref:System.IAsyncResult>旧バージョンとの互換性のためのパターン。  
  
    -   イベント ベースのパターンを公開し、<xref:System.IAsyncResult>オブジェクト モデルの結果として得られる複雑性が、実装を分離することの利点を上回る場合に、同じクラスのパターンします。 イベント ベースのパターンを公開することを避けるよりも 1 つのクラスで両方のパターンを公開することをお勧めします。  
  
    -   両方のイベント ベースのパターンを公開する必要がある場合と<xref:System.IAsyncResult>パターンは、1 つのクラスを使用して<xref:System.ComponentModel.EditorBrowsableAttribute>に設定<xref:System.ComponentModel.EditorBrowsableState.Advanced>をマークする、<xref:System.IAsyncResult>高度な機能としてのパターンの実装です。 など、デザイン環境に示すこの[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)]を表示しないように、IntelliSense、<xref:System.IAsyncResult>プロパティとメソッド。 これらのプロパティとメソッドが完全に使用可能ではまだが IntelliSense によって、開発者が API の鮮明に表示します。  
  
## <a name="criteria-for-exposing-the-iasyncresult-pattern-in-addition-to-the-event-based-pattern"></a>イベント ベースのパターンに加えて IAsyncResult パターンを公開するための条件  
 イベント ベースの非同期パターンには、前述のシナリオで多くの利点がありますがいくつかの欠点は、パフォーマンスが最も重要な要件である場合に注意してください。  
  
 イベント ベースのパターンでは取り上げませんが 3 つのシナリオはだけでなく、<xref:System.IAsyncResult>パターン。  
  
-   1 つで待機をブロック<xref:System.IAsyncResult>  
  
-   多くの待機をブロックして<xref:System.IAsyncResult>オブジェクト  
  
-   完了のポーリング、<xref:System.IAsyncResult>  
  
 イベント ベースのパターンを使用して、こうしたシナリオに対処することができますが、これは、使用するよりも煩雑、<xref:System.IAsyncResult>パターン。  
  
 開発者は多くの場合、使用して、<xref:System.IAsyncResult>通常非常に高いパフォーマンスの要件を設定しているサービスのパターン。 たとえば、完了のシナリオのポーリングは、高パフォーマンス サーバー手法です。  
  
 さらに、イベント ベースのパターンより効率が下がります、<xref:System.IAsyncResult>特に複数のオブジェクトを作成するためのパターンを<xref:System.EventArgs>、およびスレッド間で同期するためです。  
  
 次の一覧を使用する場合に実行する推奨事項を示しています、<xref:System.IAsyncResult>パターン。  
  
-   だけを公開、<xref:System.IAsyncResult>のサポートを特に必要とするときのパターンを<xref:System.Threading.WaitHandle>または<xref:System.IAsyncResult>オブジェクト。  
  
-   だけを公開、<xref:System.IAsyncResult>パターンを使用する既存の API がある場合、<xref:System.IAsyncResult>パターン。  
  
-   基づく既存の API がある場合、<xref:System.IAsyncResult>パターンも、イベント ベースのパターンで、次のリリースで公開することを検討してください。  
  
-   だけを公開<xref:System.IAsyncResult>パターンを確認する高パフォーマンスの要件がある場合は、イベント ベースのパターンで満たすことができませんが、によって満たすことができます、<xref:System.IAsyncResult>パターン。  
  
## <a name="see-also"></a>関連項目  
 [チュートリアル: イベントベースの非同期パターンをサポートするコンポーネントの実装](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [イベント ベースの非同期パターン (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)  
 [イベント ベースの非同期パターンを使用したマルチスレッド プログラミング](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [イベントベースの非同期パターンの実装](../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)  
 [イベントベースの非同期パターンを実装するための推奨される手順](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)  
 [イベントベースの非同期パターンの概要](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
