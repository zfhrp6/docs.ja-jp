---
title: "方法 : Windows フォームからリソースに埋め込まれたサウンドを再生する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "サウンドの再生 (リソースから)"
  - "サウンドの再生リソース [Windows フォーム]"
  - "リソースからのサウンドの再生"
  - "リソースからサウンドを再生 SoundPlayer クラス"
ms.assetid: 7d148bb6-8a1e-47d7-a08d-35828d2e688f
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : Windows フォームからリソースに埋め込まれたサウンドを再生する
使用することができます、 <xref:System.Media.SoundPlayer>埋め込みリソースからサウンドを再生するクラス。  
  
## <a name="example"></a>例  
 [!code-csharp[System.Windows.Forms.Sound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Sound/CS/soundtestform.cs#10)]
 [!code-vb[System.Windows.Forms.Sound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Sound/VB/soundtestform.vb#10)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
 インポート、 <xref:System.Media?displayProperty=fullName>名前空間。  
  
 プロジェクト内の埋め込みリソースとしてサウンド ファイルを含めることです。  
  
 置換"<>\>"サウンド ファイルが埋め込まれているアセンブリの名前に置き換えます。 ".Dll"サフィックスを含めないでください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Media.SoundPlayer>   
 [方法: Windows フォームからサウンドを再生](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)   
 [方法: Windows フォームでサウンドの再生をループ処理](../../../../docs/framework/winforms/controls/how-to-loop-a-sound-playing-on-a-windows-form.md)