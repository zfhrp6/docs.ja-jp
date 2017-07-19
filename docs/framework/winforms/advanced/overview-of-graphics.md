---
title: "グラフィックスについて | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "グラフィックス, 概要 (グラフィックスの)"
  - "グラフィックス, 使用 (マネージ インターフェイスを)"
ms.assetid: a602aef8-a8c8-4c36-9816-74e7bad96a68
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# グラフィックスについて
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、Microsoft Windows オペレーティング システムのサブシステムを形成するアプリケーション プログラミング インターフェイス \(API\) です。[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、情報を表示する画面およびプリンターを担当しています。  その名前からわかるように、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] の後継であり、以前のバージョンの Windows に含まれているグラフィックス デバイス インターフェイスです。  
  
## マネージ クラスのインターフェイス  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API は、マネージ コードとして配置されているクラスのセットを通じて公開されます。  このクラスのセットは [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] に対する *マネージ クラスのインターフェイス* と呼ばれます。  次の名前空間は、マネージ クラスのインターフェイスを構成します。  
  
-   <xref:System.Drawing>  
  
-   <xref:System.Drawing.Drawing2D>  
  
-   <xref:System.Drawing.Imaging>  
  
-   <xref:System.Drawing.Text>  
  
-   <xref:System.Drawing.Printing>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] などのグラフィックス デバイス インターフェイスを使用して、画面、またはプリンターに情報を表示でき、特定のディスプレイ デバイスの詳細について考慮する必要はありません。  プログラマは [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] クラスによって提供されるさまざまなメソッドを呼び出します。次に、これらのメソッドで、特定のデバイス ドライバーへの適切な呼び出しを実行します。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、グラフィックス ハードウェアからアプリケーションを分離します。この分離により、プログラマがデバイスに依存しないアプリケーションを作成できるようになります。  
  
## 参照  
 [グラフィックスの概要](../../../../docs/framework/winforms/advanced/graphics-overview-windows-forms.md)