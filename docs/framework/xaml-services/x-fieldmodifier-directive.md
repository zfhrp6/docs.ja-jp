---
title: "x:FieldModifier Directive | Microsoft Docs"
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
  - "FieldModifier attribute in XAML [XAML Services]"
  - "x:FieldModifier attribute [XAML Services]"
  - "XAML [XAML Services], x:FieldModifier attribute"
ms.assetid: ed427cd4-2f35-4d24-bd2f-0fa7b71ec248
caps.latest.revision: 15
author: "wadepickett"
ms.author: "wpickett"
manager: "wpickett"
caps.handback.revision: 14
---
# x:FieldModifier Directive
指定されているオブジェクト参照のフィールドが、既定動作の <xref:System.Reflection.TypeAttributes?displayProperty=fullName> ではなく <xref:System.Reflection.TypeAttributes?displayProperty=fullName> アクセスで定義されるように、XAML のコンパイル動作を変更します。  
  
## XAML 属性の使用方法  
  
```  
<object x:FieldModifier="Public".../>  
```  
  
## XAML 値  
  
|||  
|-|-|  
|*Public*|<xref:System.Reflection.TypeAttributes?displayProperty=fullName> か <xref:System.Reflection.TypeAttributes?displayProperty=fullName> かを指定するために渡す正確な文字列は、分離コードで使用されているプログラミング言語によって異なります。  「解説」を参照してください。|  
  
## 依存関係  
 XAML 稼動環境が任意の場所で `x:FieldModifier` を使用する場合、XAML 稼動環境のルート要素は [x:Class Directive](../../../docs/framework/xaml-services/x-class-directive.md) を宣言する必要があります。  
  
## 解説  
 `x:FieldModifier` は、クラスまたはそのメンバーの一般的なアクセス レベルの宣言には関連しません。  XAML 稼動環境の一部である特定の XAML オブジェクトが処理されるときの XAML 処理動作にだけ関係し、アプリケーションのオブジェクト グラフ内で潜在的にアクセスできるオブジェクトとなります。  既定では、このようなオブジェクトのフィールド参照は非公開なので、コントロール コンシューマーはオブジェクト グラフを直接変更できません。  代わりに、コントロール コンシューマーは、レイアウト ルートの取得、子要素のコレクションの取得、専用のパブリック プロパティの取得などのプログラミング モデルによって有効になる標準パターンを使用してオブジェクト グラフを変更します。  
  
 `x:FieldModifier` 属性の値はプログラミング言語ごとに異なり、その目的は特定のフレームワークで変わることがあります。  使用する文字列は、各言語の <xref:System.CodeDom.Compiler.CodeDomProvider> の実装方法、その言語が <xref:System.Reflection.TypeAttributes?displayProperty=fullName> と <xref:System.Reflection.TypeAttributes?displayProperty=fullName> の意味を定義するために返す型コンバーター、およびその言語が大文字と小文字を区別するかどうかによって決まります。  
  
-   [!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)] の場合、<xref:System.Reflection.TypeAttributes?displayProperty=fullName> を指定するために渡す文字列は `public` です。  
  
-   [!INCLUDE[TLA2#tla_visualbnet](../../../includes/tla2sharptla-visualbnet-md.md)] の場合、<xref:System.Reflection.TypeAttributes?displayProperty=fullName> を指定するために渡す文字列は `Public` です。  
  
-   [!INCLUDE[TLA2#tla_cppcli](../../../includes/tla2sharptla-cppcli-md.md)] の場合、XAML のターゲットは現在存在しないため、渡す文字列は定義されていません。  
  
 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> \([!INCLUDE[TLA2#tla_cshrp](../../../includes/tla2sharptla-cshrp-md.md)] では `internal`、[!INCLUDE[TLA2#tla_visualb](../../../includes/tla2sharptla-visualb-md.md)] では `Friend`\) を指定することもできますが、動作としては `NotPublic` が既定となっているため <xref:System.Reflection.TypeAttributes?displayProperty=fullName> を指定するのは一般的ではありません。  
  
 <xref:System.Reflection.TypeAttributes?displayProperty=fullName> が既定の動作になっているのは、XAML をコンパイルしたアセンブリの外部のコードから XAML で作成された要素にアクセスする必要があまりないためです。  パブリック アクセスを許可するようにユーザーが明確に `x:FieldModifier` を設定しない限り、WPF のセキュリティ アーキテクチャと XAML のコンパイル動作の組み合わせが、要素のインスタンスを格納するフィールドを Public にすることはありません。  
  
 `x:FieldModifier` は、[x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md)が指定されている要素に対してのみ関係します。これは、フィールドが Public になると、その名前を使用してフィールドを参照するためです。  
  
 ルート要素の部分クラスは既定で Public になっていますが、[x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)を使用して NonPublic にすることができます。  [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)は、ルート要素クラスのインスタンスのアクセス レベルにも影響を与えます。  ルート要素には `x:Name` と `x:FieldModifier` の両方を配置できますが、これはルート要素のパブリック フィールドのコピーを作成するだけであり、実際のルート要素クラスのアクセス レベルは引き続き [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)によって制御されます。  
  
## 参照  
 [WPF における XAML とカスタム クラス](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md)   
 [WPF における分離コードと XAML](../../../docs/framework/wpf/advanced/code-behind-and-xaml-in-wpf.md)   
 [x:Name Directive](../../../docs/framework/xaml-services/x-name-directive.md)   
 [WPF アプリケーション \(WPF\) のビルド](../../../docs/framework/wpf/app-development/building-a-wpf-application-wpf.md)   
 [x:ClassModifier Directive](../../../docs/framework/xaml-services/x-classmodifier-directive.md)