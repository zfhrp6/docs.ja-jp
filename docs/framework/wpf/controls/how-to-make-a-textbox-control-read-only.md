---
title: "方法 : TextBox コントロールを読み取り専用にする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f3d3acf1e5065633f9f4c75f24780230525b01ba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-a-textbox-control-read-only"></a>方法 : TextBox コントロールを読み取り専用にする
この例は、構成する方法を示します、<xref:System.Windows.Controls.TextBox>ユーザー入力や変更を許可しないように制御します。  
  
## <a name="example"></a>例  
 ユーザーがの内容を変更することを防止する、<xref:System.Windows.Controls.TextBox>コントロールを設定、<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>属性を**true**です。  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>属性にはユーザーの入力のみが影響します。 内のテキスト セットには影響しません、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の説明、<xref:System.Windows.Controls.TextBox>コントロール、またはプログラムから設定されたテキスト、<xref:System.Windows.Controls.TextBox.Text%2A>プロパティです。  
  
 既定値の<xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A>は**false**です。  
  
## <a name="see-also"></a>参照  
 [TextBox の概要](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox の概要](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
