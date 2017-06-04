---
title: "方法 : Windows フォームでサウンドの再生をループする | Microsoft Docs"
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
  - "再生 (サウンドを), ループ"
  - "サウンド ループ"
  - "SoundPlayer クラス, 再生ループ"
  - "サウンド, ループ"
ms.assetid: ea95dd46-10a3-46c0-8263-4b205f00df7f
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 17
---
# 方法 : Windows フォームでサウンドの再生をループする
サウンドを繰り返し再生するコード例を次に示します。  `stopPlayingButton_Click` イベント ハンドラー内のコードが実行されると、現在再生されているサウンドが停止します。  サウンドが再生されていない場合は、何も起こりません。  
  
## 使用例  
 [!code-csharp[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/CS/Form1.cs#1)]
 [!code-vb[System.Media.SoundPlayer.PlayLooping#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Media.SoundPlayer.PlayLooping/VB/Form1.vb#1)]  
  
## コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System アセンブリおよび System.Windows.Forms アセンブリへの参照  
  
-   ファイル名 `"c:\Windows\Media\chimes.wav"` を有効なファイル名に置き換えます。  
  
 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] または [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] のコマンド ラインからこの例をビルドする方法の詳細については、「[コマンド ラインからのビルド](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md)」または「[csc.exe を使用したコマンド ラインからのビルド](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」を参照してください。  また、コードを新しいプロジェクトに貼り付けることにより、[!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] でこの例をビルドすることもできます。  「[方法 : 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## 信頼性の高いプログラミング  
 ファイルの操作は、適切な例外処理ブロックで囲む必要があります。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パス名が不適切である場合。  たとえば、無効な文字が含まれている場合や、空白だけの場合などです \(<xref:System.ArgumentException> クラス\)。  
  
-   パスが読み取り専用である場合 \(<xref:System.IO.IOException> クラス\)。  
  
-   パス名が `Nothing` である場合 \(<xref:System.ArgumentNullException> クラス\)。  
  
-   パス名が長すぎる場合 \(<xref:System.IO.PathTooLongException> クラス\)。  
  
-   パスが無効である場合 \(<xref:System.IO.DirectoryNotFoundException> クラス\)。  
  
-   パスがコロン ":" のみである場合 \(<xref:System.NotSupportedException> クラス\)。  
  
## .NET Framework セキュリティ  
 ファイル名からファイルの内容を判断しないでください。  たとえば、Form1.vb というファイルは Visual Basic のソース ファイルではない可能性もあります。  アプリケーションでデータを使用する前に、入力をすべて検証してください。  
  
## 参照  
 <xref:System.Media.SoundPlayer.PlayLooping%2A>   
 [方法 : Windows フォームからサウンドを再生する](../../../../docs/framework/winforms/controls/how-to-play-a-sound-from-a-windows-form.md)   
 [SoundPlayer クラスの概要](../../../../docs/framework/winforms/controls/soundplayer-class-overview.md)