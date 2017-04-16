---
title: "方法 : グローバル アセンブリ キャッシュの内容を表示する | Microsoft Docs"
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
  - "アセンブリ [.NET Framework], グローバル アセンブリ キャッシュ"
  - "GAC (グローバル アセンブリ キャッシュ), 表示 (内容を)"
  - "Gacutil.exe"
  - "グローバル アセンブリ キャッシュ ツール"
  - "グローバル アセンブリ キャッシュ, 表示 (内容を)"
  - "一覧 (グローバル アセンブリ キャッシュ内のアセンブリの)"
  - "厳密な名前を付けたアセンブリ, グローバル アセンブリ キャッシュ"
  - "表示 (グローバル アセンブリ キャッシュ内のアセンブリを)"
ms.assetid: c5f786a0-969b-4f14-9f02-e77c3384d9af
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : グローバル アセンブリ キャッシュの内容を表示する
[グローバル アセンブリ キャッシュ ツール \(Gacutil.exe\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用すると、グローバル アセンブリ キャッシュの内容を表示できます。  
  
### グローバル アセンブリ キャッシュ内のアセンブリの一覧を表示するには、次のようにします。  
  
1.  [Visual Studio コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)で次のコマンドを入力します。  
  
     **gacutil \-l**   
     または               
     **gacutil \/l**  
  
 以前のバージョンの .NET Framework では、Windows のシェル拡張機能である [Shfusion.dll](http://msdn.microsoft.com/ja-jp/0d9464cf-ddba-4ca9-bbec-f678fb58f380) により、エクスプローラーでグローバル アセンブリ キャッシュを表示することができました。  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、Shfusion.dll は廃止されましたが、互換性のために残されています。  
  
## 参照  
 [アセンブリとグローバル アセンブリ キャッシュの使用](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [Gacutil.exe \(グローバル アセンブリ キャッシュ ツール\)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)