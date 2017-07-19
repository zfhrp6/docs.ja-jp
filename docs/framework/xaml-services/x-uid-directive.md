---
title: "x:Uid Directive | Microsoft Docs"
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
  - "XAML [XAML Services], localizable content attribute"
  - "XAML [XAML Services], x:Uid attribute"
  - "x:Uid attribute [XAML Services]"
  - "Uid attribute [XAML Services]"
ms.assetid: 81defade-483b-4a89-b76d-9b25bba34010
caps.latest.revision: 12
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 12
---
# x:Uid Directive
マークアップ要素の一意識別子を提供します。  多くの場合、この一意識別子は XAML のローカリゼーションのプロセスとツールによって使用されます。  
  
## XAML 属性の使用方法  
  
```  
<object x:Uid="identifier"... />  
```  
  
## XAML 値  
  
|||  
|-|-|  
|`identifier`|`x:Uid` コンシューマーによる解釈時にファイル内で一意であることが必要となる、手動で作成または自動生成された文字列。|  
  
## 解説  
 \[MS\-XAML\] では、`x:Uid` はディレクティブとして定義されます。  詳細については、「[\[MS\-XAML\] 第 5.3.6 節](http://go.microsoft.com/fwlink/?LinkId=114525)」を参照してください。  
  
 規定された XAML のローカリゼーション シナリオにより、`x:Uid` は `x:Name` から分離しています。したがって、ローカリゼーションで使用される識別子は、プログラミング モデルの関連において `x:Name` への依存関係はありません。  また、`x:Name` が XAML 名前スコープによって制御されるのに対して、`x:Uid` が XAML 言語で定義された一意性の適用の概念によって制御されることはありません。  一般的な意味での XAML プロセッサ \(ローカリゼーション プロセスに関与しないプロセッサ\) では、`x:Uid` 値の一意性を適用する処理は行われません。  概念上、この処理は値を作成する側の責任で行われます。  専用のグローバリゼーションのプロセスやツールなど、この値を使用する側にとっては、単一の XAML ソースに含まれる `x:Uid` 値が一意になっていると想定するのは当然のことになります。  一般的な一意性モデルでは、XAML を表現する XML でエンコードされたファイル内で `x:Uid` 値は一意になります。  
  
 特定の XAML スキーマを十分に認識するツールでは、テキスト文字列値がマークアップで検出されたすべてのケースに対してではなく、本当にローカライズ可能な文字列のみに `x:Uid` を適用するよう選択できます。  
  
 フレームワークでは、属性 <xref:System.Windows.Markup.UidPropertyAttribute> を定義元の型に適用することで、オブジェクト モデルに含まれる特定のプロパティを `x:Uid` のエイリアスとして指定できます。  フレームワークで特定のプロパティを指定する場合、同じオブジェクトで `x:Uid` とエイリアス化したメンバーの両方を指定することは無効です。  `x:Uid` とエイリアス化したメンバーの両方を指定した場合、.NET Framework XAML サービス API によって通常、このケースでは <xref:System.Xaml.XamlDuplicateMemberException> がスローされます。  
  
## WPF の使用上の注意  
 WPF ローカリゼーションのプロセスおよび XAML の BAML 形式における `x:Uid` の役割の詳細については、「[WPF のグローバリゼーション](../../../ocs/framework/wpf/advanced/globalization-for-wpf.md)」または「<xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>」を参照してください。  
  
## 参照  
 <xref:System.Windows.Markup.Localizer.BamlLocalizableResourceKey.Uid%2A>   
 <xref:Microsoft.Build.Tasks.Windows.UidManager>   
 [WPF のグローバリゼーション](../../../ocs/framework/wpf/advanced/globalization-for-wpf.md)