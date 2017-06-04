---
title: "Add Content to a Text Box Using UI Automation | Microsoft Docs"
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
  - "adding content to text boxes"
  - "text boxes, adding content"
  - "UI Automation, adding content to text boxes"
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
caps.latest.revision: 13
author: "Xansky"
ms.author: "mhopkins"
manager: "markl"
caps.handback.revision: 13
---
# Add Content to a Text Box Using UI Automation
> [!NOTE]
>  このドキュメントは、<xref:System.Windows.Automation> 名前空間で定義されているマネージ [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] クラスを使用する .NET Framework 開発者を対象としています。  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]に関する最新情報については、「[Windows Automation API: UI Automation \(Windows オートメーション API: UI オートメーション\)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックのコード例では、[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]を使用して 1 行のテキスト ボックスにテキストを挿入する方法を示します。  [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]を適用できない複数行コントロールおよびリッチ テキスト コントロールのために、別の方法も提供されています。  また、比較のために、この例では Win32 メソッドを使用して同じことを実現する方法も示します。  
  
## 使用例  
 次の例では、ターゲット アプリケーションで一連のテキスト コントロールをステップ スルーします。  各テキスト コントロールについては、<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> メソッドを使用して、各コントロールから <xref:System.Windows.Automation.ValuePattern> オブジェクトを取得できるかどうかがテストされます。  テキスト コントロールが <xref:System.Windows.Automation.ValuePattern> をサポートしていない場合は、<xref:System.Windows.Automation.ValuePattern.SetValue%2A> メソッドを使用して、ユーザー定義文字列をテキスト コントロールに挿入します。  それ以外の場合は、<xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=fullName> メソッドが使用されます。  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## 参照  
 [TextPattern Insert Text Sample](http://msdn.microsoft.com/ja-jp/67353f93-7ee2-42f2-ab76-5c078cf6ca16)