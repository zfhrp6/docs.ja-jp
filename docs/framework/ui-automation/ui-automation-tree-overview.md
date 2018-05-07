---
title: UI オートメーション ツリーの概要
ms.date: 03/30/2017
helpviewer_keywords:
- automation tree
- UI Automation, tree
ms.assetid: 03b98058-bdb3-47a0-8ff7-45e6cdf67166
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0823a569b19d46f32c1cb780470a935f20429c11
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-tree-overview"></a>UI オートメーション ツリーの概要
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 支援技術製品とテスト スクリプトは、移動、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーに関する情報を収集、[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]とその要素。  
  
 内で、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーがありますが、ルート要素 (<xref:System.Windows.Automation.AutomationElement.RootElement%2A>) を表す、現在のデスクトップとその子要素は、windows アプリケーションを表します。 これらの各子要素を表すの要素を含めることができます[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]メニュー、ボタン、ツールバー、リスト ボックスなどです。 さらに、これらの要素には、リスト項目などの要素を含めることができます。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーが、固定された構造ではなく、数千もの要素が含まれるために、その全体像で見ることはほとんどありません。 その一部は必要に応じてビルドされ、要素の追加、移動、削除に伴って変更されます。  
  
 UI オートメーション プロバイダーのサポート、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ルート (通常は、ウィンドウでホストされている) とサブツリーから成るからなるフラグメント内の項目間のナビゲーションを実装することによってツリー。 ただし、プロバイダーは、コントロール間のナビゲーションには関与しません。 によって管理されて、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]コア、既定のウィンドウ プロバイダーから情報を使用します。  
  
<a name="uiautomation_tree_view"></a>   
## <a name="views-of-the-automation-tree"></a>オートメーション ツリーのビュー  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]だけが含まれるビューを作成するツリーをフィルター処理できます<xref:System.Windows.Automation.AutomationElement>特定のクライアントに関連するオブジェクト。 このアプローチにより、クライアントで表現される構造体をカスタマイズする[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]特定のニーズにします。  
  
 クライアントがビューをカスタマイズする方法には、スコープ設定とフィルター処理の 2 つがあります。 スコープ設定では、基本要素を起点としてビューの範囲を定義します。たとえば、アプリケーションがデスクトップの直接の子だけを検索するか、アプリケーション ウィンドウのすべての子孫を検索するかを定義できます。 フィルター処理では、ビューに含める要素の種類を定義します。  
  
 UI オートメーション プロバイダーのサポートなどの要素でプロパティを定義することでフィルター処理、<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>と<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>プロパティです。  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 次の 3 つの既定のビューを提供します。 これらのビューは、実行されるフィルター処理の種類によって定義されます。すべてのビューのスコープは、アプリケーションによって定義されます。 さらに、アプリケーションではプロパティに他のフィルターを適用して、たとえば有効にされているコントロールだけをコントロール ビューに含めることもできます。  
  
<a name="uiautomation_raw_view"></a>   
### <a name="raw-view"></a>列ビュー  
 未加工のビュー、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーの完全なツリーは、<xref:System.Windows.Automation.AutomationElement>デスクトップをルート オブジェクト。 未加工ビューは、アプリケーションのネイティブ プログラムによる構造に忠実に従っているため、使用できるビューの中では最も詳細なビューです。 また、ツリーの他のビューは、未加工ビューに基づいて構築されます。 このビューが、基になる依存[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]framework, の未加工のビュー、[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]ボタンがよりも、別の未加工ビューは、[!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)]ボタンをクリックします。  
  
 未加工ビューを取得すると、プロパティを指定せずに要素を検索してまたはを使用して、<xref:System.Windows.Automation.TreeWalker.RawViewWalker>ツリーを移動します。  
  
<a name="uiautomation_control_view"></a>   
### <a name="control-view"></a>コントロール ビュー  
 コントロール ビュー、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリーを記述する支援技術製品のタスクを簡略化、[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]エンドユーザーを支援することをエンド ユーザー アプリケーションの対話に密接に対応しているため、[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]構造体エンドユーザーが認識します。  
  
 コントロール ビューは、未加工ビューのサブセットです。 すべてが含まれます[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]対話型または内のコントロールの論理構造に貢献すると、エンドユーザーが理解できるようにする、未加工ビューの項目、[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]です。 例として[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]の論理構造に貢献しているアイテム、 [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]、ただしではなく対話型自体、リスト ビューのヘッダー、ツールバー、メニューのおよびステータス バーなどの項目コンテナーは、します。 レイアウトや装飾の目的のためだけに使用される非対話型項目は、コントロール ビューには表示されません。 その一例は、パネルです。パネルは、ダイアログでコントロールをレイアウトするためだけに使用され、情報はまったく含まれません。 コントロール ビューに表示される非対話型の項目は、情報を提供するグラフィックとダイアログ内の静的テキストです。 コントロール ビューに含まれる非対話型の項目がキーボード フォーカスを受け取ることはできません。  
  
 コントロール ビューを取得するを持つ要素を検索、<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>プロパティに設定`true`、またはを使用して、<xref:System.Windows.Automation.TreeWalker.ControlViewWalker>ツリーを移動します。  
  
<a name="uiautomation_content_view"></a>   
### <a name="content-view"></a>コンテンツ ビュー  
 コンテンツ ビュー、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ツリー コントロールのビューのサブセットであります。 含まれている[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]、ユーザー インターフェイスで実際の情報を伝達する項目を含む[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]受け取ることができる項目がキーボード フォーカスとテキストのラベルではありませんが、[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]項目。 たとえば、ドロップダウン コンボ ボックス内の値は、エンドユーザーが使用する情報を表すため、コンテンツ ビューに表示されます。 コンテンツ ビューで、コンボ ボックスとリスト ボックスは両方として表されますのコレクション[!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]項目おそらく複数、または 1 つの項目を選択できます。 コンテンツ ビューの目的は、ユーザーに提示するデータ (つまりコンテンツ) を表示することなので、このビューは、どの項目が常に開かれていて、どの項目が展開または折りたたむことができるかは重要ではありません。  
  
 コンテンツ ビューを取得するを持つ要素を検索、<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>プロパティに設定`true`、またはを使用して、<xref:System.Windows.Automation.TreeWalker.ContentViewWalker>ツリーを移動します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Automation.AutomationElement>  
 [UI オートメーションの概要](../../../docs/framework/ui-automation/ui-automation-overview.md)
