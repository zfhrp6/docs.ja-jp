---
title: "UI オートメーションを使用した、埋め込みオブジェクトへのアクセス"
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
- embedded objects, accessing
- accessing embedded objects
- UI Automation, accessing embedded objects
ms.assetid: a5b513ec-7fa6-4460-869f-c18ff04f7cf2
caps.latest.revision: "17"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0f417acd3440c224db06ca4034c23a1cd6eb395e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="access-embedded-objects-using-ui-automation"></a>UI オートメーションを使用した、埋め込みオブジェクトへのアクセス
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI オートメーション](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックでは、どのように [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] を使用して、テキスト コントロールのコンテンツ内に埋め込みオブジェクトを公開できるのかを示しています。  
  
> [!NOTE]
>  埋め込みオブジェクトには、イメージ、ハイパーリンク、ボタン、テーブル、ActiveX コントロールを含めることができます。  
  
 埋め込みオブジェクトは、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] テキスト プロバイダーの子と見なされます。 これにより、他のすべての [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] 要素と同じ UI オートメーション ツリーの構造を介して公開することができます。 次に、機能は、埋め込みオブジェクトのコントロール型で通常必要とされるコントロール パターンを通じて公開されます (たとえば、ハイパーリンクはテキスト ベースであるため、 <xref:System.Windows.Automation.TextPattern>をサポートします)。  
  
 ![テキスト コンテナー内の埋め込みオブジェクト。] (../../../docs/framework/ui-automation/media/uia-textpattern-embeddedobjects.PNG "UIA_TextPattern_EmbeddedObjects")  
サンプル ドキュメントのテキスト コンテンツ、(「ご存知でしたか。」[...])2 つの埋め込みオブジェクト (クジラとテキストのハイパーリンクの画像)、コード例については、ターゲットとして使用します。  
  
## <a name="example"></a>例  
 次のコード例は、 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] テキスト プロバイダー内から埋め込みオブジェクトのコレクションを取得する方法を示します。 概要で提供されたサンプルのドキュメントについては、2 つのオブジェクトが返されます (イメージ要素と、テキスト要素)。  
  
> [!NOTE]
>  イメージ要素には、画像に関連付けられて説明する組み込みテキストが必要であり、通常は <xref:System.Windows.Automation.AutomationElement.NameProperty> 内にあります (「青いクジラ」など)。 ただし、イメージ オブジェクトにまたがるテキスト範囲を取得すると、イメージもこの説明のテキストもテキストのストリームで返されません。  
  
 [!code-csharp[FindText#StartApp](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#startapp)]
 [!code-vb[FindText#StartApp](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#startapp)]  
[!code-csharp[FindText#FindTextProvider](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#findtextprovider)]
[!code-vb[FindText#FindTextProvider](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#findtextprovider)]  
[!code-csharp[FindText#GetChildren](../../../samples/snippets/csharp/VS_Snippets_Wpf/FindText/CSharp/SearchWindow.cs#getchildren)]
[!code-vb[FindText#GetChildren](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FindText/VisualBasic/SearchWindow.vb#getchildren)]  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] テキスト プロバイダー内の埋め込みオブジェクトからテキストの範囲を取得する方法を、次のコード例で示します。 取得されるテキストの範囲は空の範囲です。ここで、開始エンドポイントは "… ocean.(space)" の後に続き、終了エンドポイントは、(概要で提供した画像に示されているように) 埋め込みハイパーリンクを表す終了の "." に先行します。 これは空の範囲ですが、スパンが 0 ではないため、低次元テキスト範囲とはみなされません。  
  
> [!NOTE]
>  <xref:System.Windows.Automation.TextPattern> はハイパーリンクなどのテキスト ベースの埋め込みオブジェクトを取得することができます。ただし、セカンダリ <xref:System.Windows.Automation.TextPattern> は完全な機能を公開するために、埋め込みオブジェクトから取得する必要があります。  
  
 [!code-csharp[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIATextPattern_snip/CSharp/SearchWindow.cs#getrangefromchild)]
 [!code-vb[UIATextPattern_snip#GetRangeFromChild](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIATextPattern_snip/VisualBasic/SearchWindow.vb#getrangefromchild)]  
  
## <a name="see-also"></a>関連項目  
 [UI オートメーション TextPattern の概要](../../../docs/framework/ui-automation/ui-automation-textpattern-overview.md)  
 [UI オートメーション コントロール パターンの概要](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [クライアントの UI オートメーション コントロール パターン](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [UI オートメーションを使用してテキスト ボックスにコンテンツを追加します。](../../../docs/framework/ui-automation/add-content-to-a-text-box-using-ui-automation.md)  
 [検索し、UI オートメーションを使用してテキストを強調表示](../../../docs/framework/ui-automation/find-and-highlight-text-using-ui-automation.md)
