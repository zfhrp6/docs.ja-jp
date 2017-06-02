---
title: "依存関係プロパティのセキュリティ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "依存関係プロパティ, access"
  - "依存関係プロパティ, セキュリティ"
  - "セキュリティ, 依存関係プロパティ"
  - "セキュリティ, ラッパー"
  - "検証, 依存関係プロパティ"
  - "ラッパー, access"
  - "ラッパー, セキュリティ"
ms.assetid: d10150ec-90c5-4571-8d35-84bafa2429a4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 依存関係プロパティのセキュリティ
依存関係プロパティは一般に、パブリック プロパティと見なす必要があります。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] プロパティ システムの性質上、依存関係プロパティ値については、セキュリティは保証されません。  
  
   
  
<a name="AccessSecurity"></a>   
## ラッパーと依存関係プロパティのアクセスとセキュリティ  
 通常、依存関係プロパティは、インスタンスのプロパティの取得や設定を簡素化する "ラッパー" [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティと共に実装されます。  ただし、ラッパーは、依存関係プロパティと対話する場合に使用される基になる <xref:System.Windows.DependencyObject.GetValue%2A> および <xref:System.Windows.DependencyObject.SetValue%2A> の各静的呼び出しを実装する便利な方法です。  別な観点で考えると、プロパティは、プライベート フィールドではなく依存関係プロパティによって偶然にサポートされている[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] プロパティとして公開されています。  ラッパーに適用されるセキュリティ機構は、基になる依存関係プロパティに関するプロパティ システムの動作およびアクセスと同等ではありません。  ラッパーに対してセキュリティを要求しても、この便利な方法が使用できなくなるだけで、<xref:System.Windows.DependencyObject.GetValue%2A> や <xref:System.Windows.DependencyObject.SetValue%2A> の呼び出しは阻止されません。  同様に、ラッパーに保護またはプライベート アクセス レベルを設定しても、効果的なセキュリティは実現されません。  
  
 独自の依存関係プロパティを記述する場合は、ラッパーと <xref:System.Windows.DependencyProperty> 識別子フィールドをパブリック メンバーとして宣言する必要があります。そうすることで、呼び出し元がそのプロパティの実際のアクセス レベルに関する、誤りの原因となる情報を取得することを防止できます \(そのストアが依存関係プロパティとして実装されているため\)。  
  
 カスタム依存関係プロパティの場合、そのプロパティを読み取り専用の依存関係プロパティとして登録できます。これは、そのプロパティの <xref:System.Windows.DependencyPropertyKey> への参照を保持していなくてもだれでもプロパティを設定できるのを防ぐ有効な手段となります。  詳細については、「[読み取り専用の依存関係プロパティ](../../../../docs/framework/wpf/advanced/read-only-dependency-properties.md)」を参照してください。  
  
> [!NOTE]
>  <xref:System.Windows.DependencyProperty> 識別子フィールドをプライベートとして宣言することは、禁止されていないだけでなく、カスタム クラスの直接公開名前空間を減らすのに役立つ可能性もあります。ただし、このようなプロパティは、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] 言語定義と同じ意味で "プライベート" であると見なすことはできません。その理由は次のセクションで説明します。  
  
<a name="PropertySystemExposure"></a>   
## 依存関係プロパティのプロパティ システムによる公開  
 <xref:System.Windows.DependencyProperty> をパブリック以外のアクセス レベルとして宣言することは、一般的には役に立たず、誤りの原因となる可能性もあります。  このようなアクセス レベル設定を行っても、宣言しているクラスからインスタンスへの参照を取得できなくなるだけです。  しかしプロパティ システムには、クラスのインスタンスや派生クラスのインスタンスに存在する特定のプロパティを識別する手段として <xref:System.Windows.DependencyProperty> を返すいくつかの局面があり、この識別子は、元の静的識別子がパブリック以外として宣言されていた場合でも、<xref:System.Windows.DependencyObject.SetValue%2A> の呼び出しで使用できます。  また、<xref:System.Windows.DependencyObject.OnPropertyChanged%2A> 仮想メソッドは、値が変更された既存の依存関係プロパティに関する情報を受け取ります。  さらに、<xref:System.Windows.DependencyObject.GetLocalValueEnumerator%2A> メソッドは、値がローカルに設定されたインスタンスのプロパティに関する識別子を返します。  
  
### 検証とセキュリティ  
 <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> に対して要求を発行し、要求エラーの発生時に検証エラーでプロパティの設定を回避する方法は、十分なセキュリティ機構ではありません。  <xref:System.Windows.DependencyProperty.ValidateValueCallback%2A> による設定値の無効化も、悪意のある呼び出し元がアプリケーション ドメイン内で動作している場合には、これらの呼び出し元によって抑制される可能性があります。  
  
## 参照  
 [カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)