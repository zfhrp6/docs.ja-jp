---
title: "GDI+ でのメタファイル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2b9d378f82b2a7edca00fedaacdcc0fca179c5a0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="metafiles-in-gdi"></a>GDI+ でのメタファイル
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]提供、<xref:System.Drawing.Imaging.Metafile>クラスを記録してメタファイルを表示できるようにします。 ベクター イメージとも呼ばれる、メタファイルは、コマンドと設定の描画のシーケンスとして格納されているイメージです。 コマンドと設定に記録、<xref:System.Drawing.Imaging.Metafile>オブジェクトをメモリに格納されているか、ファイルまたはストリームに保存します。  
  
## <a name="metafile-formats"></a>メタファイルの形式  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]次の形式で格納されているメタファイルを表示できます。  
  
-   Windows のメタファイル (WMF)  
  
-   拡張メタファイル (EMF)  
  
-   EMF +  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]WMF の形式ではなく、EMF と EMF + の形式で、メタファイルを記録できます。  
  
 EMF + は、拡張機能により、EMF[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]レコードが格納されます。 EMF + 形式に 2 つのバリエーションがあります: EMF + デュアルと EMF + のみです。 メタファイル EMF + だけのみを含める[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]レコード。 このようなメタファイルはによって表示されることができます[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]がなく、[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]です。 EMF + デュアル メタファイルを含む[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]と[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]レコード。 各[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]EMF + デュアルでレコード メタファイルとペアになる代替[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]レコード。 このようなメタファイルはによって表示されることができます[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]または[!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]です。  
  
 次の例では、ファイルとして保存されているメタファイルを表示します。 左上隅のメタファイルが表示されます (100, 100)。  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>参照  
 [イメージ、ビットマップ、メタファイル](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
