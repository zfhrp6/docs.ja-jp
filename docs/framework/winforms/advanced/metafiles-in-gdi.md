---
title: "GDI+ でのメタファイル | Microsoft Docs"
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
  - "GDI+, メタファイル"
  - "イメージ [Windows フォーム], メタファイル"
  - "メタファイル"
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# GDI+ でのメタファイル
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] には、メタファイルの記録および表示のために <xref:System.Drawing.Imaging.Metafile> クラスが用意されています。  メタファイルは、一連の描画コマンドおよび描画設定として格納されるイメージで、ベクター イメージと呼ばれることもあります。  <xref:System.Drawing.Imaging.Metafile> オブジェクトに記録されるコマンドと設定は、メモリに格納したり、ファイルやストリームに保存したりできます。  
  
## メタファイルの形式  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、次の形式で格納されたメタファイルを表示できます。  
  
-   WMF \(Windows メタファイル\)  
  
-   EMF \(拡張メタファイル\)  
  
-   EMF\+  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] は、EMF 形式と EMF\+ 形式でメタファイルを記録できますが、WMF 形式では記録できません。  
  
 EMF\+ は EMF の拡張機能であり、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] レコードを格納できます。  EMF\+ 形式には、EMF\+ Only と EMF\+ Dual の 2 種類があります。  EMF\+ Only メタファイルは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] レコードだけを格納します。  このメタファイルは [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では表示できますが、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] では表示できません。  EMF\+ Dual メタファイルは、[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]レコードと [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] レコードを格納します。  EMF\+ Dual メタファイル内の各 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] レコードは、代替の [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] レコードとペアになります。  このメタファイルは [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] または [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] で表示できます。  
  
 以前にファイルとして保存されたメタファイルを表示する例を次に示します。  このメタファイルは、左上隅の座標を \(100, 100\) として表示されます。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## 参照  
 [イメージ、ビットマップ、およびメタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)