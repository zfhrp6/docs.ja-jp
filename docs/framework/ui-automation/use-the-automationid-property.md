---
title: AutomationID プロパティの使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- AutomationId property
- UI Automation, AutomationId property
- properties, AutomationId
ms.assetid: a24e807b-d7c3-4e93-ac48-80094c4e1c90
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: bd5985dd531b13ca91efd9c0aa7987ff6a57e56a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="use-the-automationid-property"></a>AutomationID プロパティの使用
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックには、 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> を使用して [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ツリー内の要素を配置する方法とタイミングを示すシナリオおよびサンプル コードが記載されています。  
  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> は、UI オートメーション要素をその兄弟から一意に識別します。 コントロール ID に関連するプロパティの識別子の詳細については、「 [UI Automation Properties Overview](../../../docs/framework/ui-automation/ui-automation-properties-overview.md)」を参照してください。  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> では、ツリー全体で一意の ID は保証されません。これが役に立つには、通常、コンテナーとスコープ情報が必要です。 たとえば、アプリケーションには複数のトップレベルのメニュー項目を持つメニュー コントロールが含まれ、さらに、それらのメニュー項目に複数の子メニュー項目が含まれている場合があります。 これらの 2 次メニュー項目は、"Item1"、"Item 2" などの汎用スキームで識別され、トップレベルのメニュー項目間で子の識別子が重複することがあります。  
  
## <a name="scenarios"></a>シナリオ  
 要素を検索するときに、正確で一貫性のある結果を実現するために <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> の使用を必要とする 3 つの主な UI オートメーション クライアント アプリケーションのシナリオが識別されています。  
  
> [!NOTE]
>  <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> をサポートしているのは、最上位のアプリケーション ウィンドウ以外のコントロール ビューにあるすべての UI オートメーション要素、ID または x:Uid を持たない [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] コントロールから派生した UI オートメーション要素、およびコントロール ID を持たない [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] コントロールから派生した UI オートメーション要素です。  
  
#### <a name="use-a-unique-and-discoverable-automationid-to-locate-a-specific-element-in-the-ui-automation-tree"></a>一意で探索可能な AutomationID を使用して UI オートメーション ツリーで特定の要素を検索する  
  
-   [!INCLUDE[TLA#tla_uispy](../../../includes/tlasharptla-uispy-md.md)] などのツールを使用して関心のある <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty> 要素の [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] をレポートします。 この値をコピーし、その後の自動テストのテスト スクリプトなどのクライアント アプリケーションに貼り付けることができます。 この方法により、実行時に要素を特定して検索するために必要なコードを削減して簡略化します。  
  
> [!CAUTION]
>  通常、 <xref:System.Windows.Automation.AutomationElement.RootElement%2A>の直接の子のみの取得を試行する必要があります。 子孫の検索は、数百または数千もの要素を反復処理する場合があり、スタック オーバーフローを引き起こす可能性があります。 下位レベルの特定の要素を取得しようとする場合、アプリケーション ウィンドウから、または下位レベルのコンテナーから検索を開始する必要があります。  
  
 [!code-csharp[UIAAutomationID_snip#100](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#100)]
 [!code-vb[UIAAutomationID_snip#100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#100)]  
  
#### <a name="use-a-persistent-path-to-return-to-a-previously-identified-automationelement"></a>永続的なパスを使用して、既に特定されている AutomationElement に戻る  
  
-   クライアント アプリケーションは (単純なテスト スクリプトから、堅牢な記録と再生のためのユーティリティまで)、ファイルを開くダイアログやメニュー項目など、現在インスタンス化されていないために UI オートメーション ツリーに存在しない要素にアクセスしなければならないことがあります。 これらの要素をインスタンス化するには、AutomationID、コントロール パターンとイベント リスナーなどの [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] プロパティを使用することで、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] アクションの特定のシーケンスを再現または「再生」する必要があります。 参照してください[スクリプト ジェネレーターのサンプルのテスト](http://msdn.microsoft.com/library/028467fd-2980-4691-9522-0131dcef23a0)を使用する例については[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]との対話をユーザーに基づくテスト スクリプトを生成する、[!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)]です。  
  
 [!code-csharp[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#uiaworkerthread)]
 [!code-vb[UIAAutomationID_snip#UIAWorkerThread](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#uiaworkerthread)]  
[!code-csharp[UIAAutomationID_snip#Playback](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAAutomationID_snip/CSharp/FindByAutomationID.xaml.cs#playback)]
[!code-vb[UIAAutomationID_snip#Playback](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAAutomationID_snip/VisualBasic/FindByAutomationID.xaml.vb#playback)]  
  
#### <a name="use-a-relative-path-to-return-to-a-previously-identified-automationelement"></a>相対パスを使用して、既に特定されている AutomationElement に戻る  
  
-   特定の状況では、AutomationID が兄弟間でのみ一意であることが保証されているので、UI オートメーション ツリー内の複数の要素が同一の AutomationID プロパティの値を持っていることがあります。 このような場合、親 (または必要に応じて親の親) に基づいて、要素を一意に識別できます。 たとえば、開発者が複数のメニュー項目を持ち、それぞれに複数の子メニュー項目があるメニュー バーを提供するとします。ここで、子は "Item1"、"Item2" など、シーケンシャルの AutomationID で識別されます。 各メニュー項目は、それ自体の AutomationID と、その親の AutomationID (必要に応じて親の親の AutomationID も) によって一意に識別されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>  
 [UI Automation ツリーの概要](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [プロパティ条件に基づく UI オートメーション要素の検索](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
