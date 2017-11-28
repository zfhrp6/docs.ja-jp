---
title: "UI オートメーションを使用してテキスト属性を取得する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- getting, text attributes
- UI Automation, getting text attributes
- text attributes, getting
ms.assetid: fdefc6c3-b836-4cfe-8dec-1484bfdc5551
caps.latest.revision: "13"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: c95fbbe2917261e6b8a4a911a7ea5978da00d662
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="obtain-text-attributes-using-ui-automation"></a>UI オートメーションを使用してテキスト属性を取得する
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックでは、 [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] を使用して、テキスト範囲からテキスト属性を取得する方法について説明します。 テキスト範囲は、ドキュメント内のキャレットの現在の位置 (または低次元選択)、テキストの連続した選択、非連続のテキスト選択のコレクション、またはドキュメントのテキスト コンテンツ全体に対応します。  
  
## <a name="example"></a>例  
 次のコード例は、テキスト範囲から <xref:System.Windows.Automation.TextPattern.FontNameAttribute> を取得する方法を示しています。  
  
 [!code-csharp[UIATextPattern_snip#StartTarget](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#starttarget)]
 [!code-vb[UIATextPattern_snip#StartTarget](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#starttarget)]  
[!code-csharp[UIATextPattern_snip#GetTextElement](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#gettextelement)]
[!code-vb[UIATextPattern_snip#GetTextElement](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#gettextelement)]  
[!code-csharp[UIATextPattern_snip#FontName](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#fontname)]
[!code-vb[UIATextPattern_snip#FontName](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#fontname)]  
  
 <xref:System.Windows.Automation.TextPattern> コントロール パターンは <xref:System.Windows.Automation.Text.TextPatternRange> クラスと連携して、基本のテキスト属性、プロパティ、メソッドをサポートします。 <xref:System.Windows.Automation.TextPattern> または <xref:System.Windows.Automation.Text.TextPatternRange> によってサポートされないコントロール固有の機能の場合、 <xref:System.Windows.Automation.AutomationElement>クラスは対応するネイティブ オブジェクト モデルにアクセスするための UI オートメーション クライアントのメソッドを提供します。  
  
## <a name="see-also"></a>関連項目  
 [UI オートメーション TextPattern の概要](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [UI オートメーションを使用してテキスト ボックスにコンテンツを追加します。](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [検索し、UI オートメーションを使用してテキストを強調表示](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)  
 [UI オートメーション コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI オートメーションを使用して混合テキスト属性の詳細を取得します。](../../../docs/framework/ui-automation/obtain-mixed-text-attribute-details-using-ui-automation.md)
