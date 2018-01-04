---
title: "方法 : GroupBox テンプレートを定義する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a63a79b298a45b4efd6d1cbd439d208744358ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-groupbox-template"></a>方法 : GroupBox テンプレートを定義する
この例のテンプレートを作成する方法を示しています、<xref:System.Windows.Controls.GroupBox>コントロール。  
  
## <a name="example"></a>例  
 次の例では定義、<xref:System.Windows.Controls.GroupBox>コントロール テンプレートを使用して、<xref:System.Windows.Controls.Grid>レイアウトを制御します。 テンプレートを使用して、<xref:System.Windows.Controls.BorderGapMaskConverter>の枠線を定義する、<xref:System.Windows.Controls.GroupBox>境界線が見えにくくならないように、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A>コンテンツ。  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Controls.GroupBox>  
 [GroupBox 操作方法に関するトピック](http://msdn.microsoft.com/en-us/7692e155-a4c6-428c-b7e0-64b3740daca7)
