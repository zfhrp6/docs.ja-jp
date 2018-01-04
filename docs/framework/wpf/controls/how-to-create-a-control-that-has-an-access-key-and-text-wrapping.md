---
title: "方法 : アクセス キーおよびテキスト折り返し機能を持つコントロールを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- access keys [WPF], control for
- controls [WPF], text wrapping
- wrapping text [WPF]
- keys [WPF], control for
- controls [WPF], access keys
- text wrapping [WPF]
ms.assetid: 205099d9-2551-4302-a25e-a15af9f67e04
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 428d8febe5a789f22eef97301fca3aa4b22f25b2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-control-that-has-an-access-key-and-text-wrapping"></a>方法 : アクセス キーおよびテキスト折り返し機能を持つコントロールを作成する
この例では、アクセス キーがありテキスト折り返しをサポートするコントロールを作成する方法を説明します。 この例では、<xref:System.Windows.Controls.Label>これらの概念を説明するために管理します。  
  
## <a name="example"></a>例  
 **ラベルにテキスト折り返し機能を追加する**  
  
 <xref:System.Windows.Controls.Label>コントロールがテキストの折り返しをサポートしていません。 複数の行を折り返せるラベルが必要な場合には、テキスト折り返し機能をサポートしている別の要素を入れ子にすることができます。 次の例を使用する方法を示しています、<xref:System.Windows.Controls.TextBlock>数行のテキストをラップするラベルにします。  
  
 [!code-xaml[LabelSnippet#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#5)]  
  
 **アクセス キーおよびテキスト折り返し機能をラベルに追加する**  
  
 必要がある場合、<xref:System.Windows.Controls.Label>アクセス キー (ニーモニック) を持つを使用して、<xref:System.Windows.Controls.AccessText>要素内にある、<xref:System.Windows.Controls.Label>です。  
  
 などのコントロール<xref:System.Windows.Controls.Label>、 <xref:System.Windows.Controls.Button>、 <xref:System.Windows.Controls.RadioButton>、 <xref:System.Windows.Controls.CheckBox>、 <xref:System.Windows.Controls.MenuItem>、 <xref:System.Windows.Controls.TabItem>、 <xref:System.Windows.Controls.Expander>、および<xref:System.Windows.Controls.GroupBox>コントロールの既定のテンプレートがあります。 これらのテンプレートが含まれて、<xref:System.Windows.Controls.ContentPresenter>です。 設定できるプロパティの 1 つ、<xref:System.Windows.Controls.ContentPresenter>は<xref:System.Windows.Controls.ContentPresenter.RecognizesAccessKey%2A>="true"、コントロールのアクセス キーの指定に使用できます。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Controls.Label>アクセス キーがあり、テキストの折り返しをサポートします。 テキストの折り返しを例のセットを有効にする、<xref:System.Windows.Controls.AccessText.TextWrapping%2A>下線付きのアクセス キーを指定する文字使用してプロパティです。 (下線文字の直後の文字はアクセス キーになります。)  
  
 [!code-xaml[LabelSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LabelSnippet/CS/Pane1.xaml#4)]  
  
## <a name="see-also"></a>参照  
 [方法: ラベルのターゲット プロパティを設定する](http://msdn.microsoft.com/en-us/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)
