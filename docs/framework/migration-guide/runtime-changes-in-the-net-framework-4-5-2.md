---
title: ".NET Framework 4.5.2 におけるランタイムの変更点 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 94ac01ea-8b12-44d2-b12b-5220a5d14d87
caps.latest.revision: 5
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 5
---
# .NET Framework 4.5.2 におけるランタイムの変更点
まれに、ランタイムの変更が、.NET Framework の以前のバージョンを対象とするものの、.NET Framework 4.5.2 ランタイムで実行される既存のアプリに影響を与える可能性があります。 次の領域の変更が含まれています。  
  
-   [ASP.NET](#ASP_NET)  
  
-   [Entity Framework](#EF)  
  
<a name="ASP_NET"></a>   
## ASP.NET ランタイムの変更  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|[ページ要素](http://msdn.microsoft.com/ja-jp/4123bb66-3fe4-4d62-b70e-33758656b458)の `enableViewStateMac` 属性|ASP.NET では開発者による次の指定ができなくなりました。<br /><br /> `<pages enableViewStateMac="false" />`<br /><br /> または<br /><br /> `<@Page EnableViewStateMac="false" %>`|ビュー ステートのメッセージ認証コード \(MAC\) は、ビュー ステートが埋め込まれたすべての要求に強制されています。<xref:System.Web.UI.Page.EnableViewStateMac%2A> プロパティを明示的に `false` に設定するアプリだけが影響されます。<br /><br /> 詳細については、「[ビュー ステートのメッセージ認証コード \(MAC\) エラーの解決](http://support.microsoft.com/kb/2915218)」を参照してください。|Major|  
  
<a name="EF"></a>   
## Entity Framework ランタイムの変更  
  
|機能|変更|影響|スコープ|  
|--------|--------|--------|----------|  
|QueryView での関係|クエリの一部として関連エンティティを含めようとする 0..1 ナビゲーション プロパティを使用して QueryView に関係するクエリをアプリが実行する場合 \(例: <xref:System.StackOverflowException> の呼び出し\) に、Entity Framework は `.Include(e=>e.RelatedNavProp)` 例外をスローしなくなります。|この変更は、`.Include` を呼び出すクエリの実行時に 1 \- 0..1 の関係にある QueryViews を使用するコードにのみ影響を与えます。 これにより信頼性が向上し、ほとんどすべてのアプリに対して透過的になります。 ただし、予期しない動作が発生する場合、次のエントリをアプリの構成ファイルの `<appSettings>` セクションに追加することにより、この変更を無効にできます。<br /><br /> `<add key="EntityFramework_SimplifyUserSpecifiedViews"  value="false" />`|エッジ|  
  
## 参照  
 [再ターゲットの変更点](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-5-2.md)   
 [4.5 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5.md)   
 [4.5.1 のアプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-5-1.md)