---
title: "UI オートメーション ツリーの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "オートメーション ツリー"
  - "UI オートメーション、ツリー"
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
caps.latest.revision: 25
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 25
---
# UI オートメーション ツリーの概要
> [!NOTE]
>  このドキュメントが目的とする、管理を使用する .NET Framework 開発者[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]で定義されたクラス、 <xref:System.Windows.Automation>名前空間。 最新情報について[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を参照してください[Windows Automation API: UI 自動化](http://go.microsoft.com/fwlink/?LinkID=156746)します。  
  
 支援技術製品やテスト スクリプトは、移動、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーに関する情報を収集するために、[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]とその要素。  
  
 内で、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーがありますが、ルート要素 (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) を表す現在のデスクトップと子要素は、アプリケーション ウィンドウを表します。 これらの各子要素を表すの要素を含めることができます[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]メニューのボタン、ツールバー、およびリスト ボックスなどです。 さらに、これらの要素には、リスト項目などの要素を含めることができます。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーは、固定構造ではないと、何千もの要素を含めることがあるため、全体的なでほとんど見します。 その一部は必要に応じてビルドされ、要素の追加、移動、削除に伴って変更されます。  
  
 UI オートメーション プロバイダーのサポート、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]はルート (通常はウィンドウでホストされている) と、サブツリーのフラグメント内の項目間のナビゲーションを実装することによってツリーです。 ただし、プロバイダーは、コントロール間のナビゲーションには関与しません。 によって管理されて、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]コアの既定のウィンドウのプロバイダーから情報を使用します。  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>オートメーション ツリーのビュー  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]だけを含むビューを作成するツリーをフィルター処理できます<xref:System.Windows.Automation.AutomationElement>特定のクライアントに関連するオブジェクト。 このアプローチにより、クライアントで表示される構造をカスタマイズする[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ニーズに合わせて特定します。  
  
 クライアントがビューをカスタマイズする方法には、スコープ設定とフィルター処理の&2; つがあります。 スコープ設定では、基本要素を起点としてビューの範囲を定義します。たとえば、アプリケーションがデスクトップの直接の子だけを検索するか、アプリケーション ウィンドウのすべての子孫を検索するかを定義できます。 フィルター処理では、ビューに含める要素の種類を定義します。  
  
 UI オートメーション プロバイダーのサポートなどの要素のプロパティを定義することでフィルター処理、 <xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>と<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>プロパティです。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]次の&3; つの既定のビューを提供します。 これらのビューは、実行されるフィルター処理の種類によって定義されます。すべてのビューのスコープは、アプリケーションによって定義されます。 さらに、アプリケーションではプロパティに他のフィルターを適用して、たとえば有効にされているコントロールだけをコントロール ビューに含めることもできます。  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>列ビュー  
 未加工のビュー、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーの完全なツリーは、 <xref:System.Windows.Automation.AutomationElement>デスクトップをルート オブジェクトです。 未加工ビューは、アプリケーションのネイティブ プログラムによる構造に忠実に従っているため、使用できるビューの中では最も詳細なビューです。 また、ツリーの他のビューは、未加工ビューに基づいて構築されます。 このビューが、基になる依存[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]フレームワークの未加工のビュー、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]さまざまな未加工のビューよりも作成したボタンも、 [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]  ボタンをクリックします。  
  
 プロパティを指定せずに要素を検索して、またはを使用して、未加工のビューが取得した、 <xref:System.Windows.Automation.TreeWalker.RawViewWalker>ツリー内で移動します。  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>コントロール ビュー  
 コントロールのビューの[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーを記述する支援技術製品のタスクを簡略化、[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]エンドユーザーを支援することをエンドユーザーとやり取りするアプリケーションに密接にマッピングされるため、[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]エンドユーザーによって認識される構造体。  
  
 コントロール ビューは、未加工ビューのサブセットです。 すべてが含まれています[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]対話型または内のコントロールの論理構造に関係するいると、エンドユーザーが理解できるように未加工のビューの項目を[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]です。 例として[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]の論理的な構造に影響するアイテム、[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]は対話型自体では、ヘッダーを一覧表示する、ツールバー、メニューのおよびステータス バーなどの項目のコンテナーです。 レイアウトや装飾の目的のためだけに使用される非対話型項目は、コントロール ビューには表示されません。 その一例は、パネルです。パネルは、ダイアログでコントロールをレイアウトするためだけに使用され、情報はまったく含まれません。 コントロール ビューに表示される非対話型の項目は、情報を提供するグラフィックとダイアログ内の静的テキストです。 コントロール ビューに含まれる非対話型の項目がキーボード フォーカスを受け取ることはできません。  
  
 コントロールのビューを持つ要素を検索して取得した、 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>プロパティに設定`true`、またはを使用して、 <xref:System.Windows.Automation.TreeWalker.ControlViewWalker>ツリー内で移動します。  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>コンテンツ ビュー  
 コンテンツ ビュー、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリー コントロールのビューのサブセットであります。 含まれている[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]ユーザー インターフェイスで真の情報を伝達する項目を含む[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]が受信可能な項目はキーボード フォーカスとなんらかのテキストのラベルではありませんが、[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]項目。 たとえば、ドロップダウン コンボ ボックス内の値は、エンドユーザーが使用する情報を表すため、コンテンツ ビューに表示されます。 コンテンツ ビューにコンボ ボックスやリスト ボックスが両方とものコレクションとして表さ[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]項目の&1; つ以上、または&1; つの項目を選択できます。 コンテンツ ビューの目的は、ユーザーに提示するデータ (つまりコンテンツ) を表示することなので、このビューは、どの項目が常に開かれていて、どの項目が展開または折りたたむことができるかは重要ではありません。  
  
 コンテンツ ビューを持つ要素を検索して取得した、 <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>プロパティに設定`true`、またはを使用して、 <xref:System.Windows.Automation.TreeWalker.ContentViewWalker>ツリー内で移動します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Automation.AutomationElement>   
 [UI オートメーションの概要](../../../docs/framework/ui-automation/ui-automation-overview.md)