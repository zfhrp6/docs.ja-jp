---
title: "方法 : Windows フォームからサウンドを再生する | Microsoft Docs"
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
  - "Windows フォームのサウンドを再生"
  - "サウンドの再生"
  - "SoundPlayer クラス"
  - "サウンド"
  - "My.Computer.Audio オブジェクト、サウンドの再生"
  - "サウンドの例 [Windows フォーム]"
ms.assetid: 3d3350b7-1ebd-4e05-a738-48ca1160a19d
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : Windows フォームからサウンドを再生する
この例では、実行時に指定されたパスでサウンドを再生します。  
  
## <a name="example"></a>例  
  
```vb  
Sub PlaySimpleSound()  
    My.Computer.Audio.Play("c:\Windows\Media\chimes.wav")  
End Sub  
```  
  
```csharp  
private void playSimpleSound()  
{  
    SoundPlayer simpleSound = new SoundPlayer(@"c:\Windows\Media\chimes.wav");  
    simpleSound.Play();  
}  
```  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   ファイル名 `"c:\Windows\Media\chimes.wav"` を有効なファイル名に置き換えます。  
  
-   (C#)参照、 <xref:System.Media?displayProperty=fullName>名前空間。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 ファイル操作は、適切な構造化例外処理ブロックで囲む必要があります。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   パス名が不適切である場合。 たとえば、無効な文字が含まれていますか、空白だけが (<xref:System.ArgumentException>クラス)。  
  
-   パスは読み取り専用 (<xref:System.IO.IOException>クラス)。  
  
-   パス名が`null`(<xref:System.ArgumentNullException>クラス)。  
  
-   パス名が長すぎます (<xref:System.IO.PathTooLongException>クラス)。  
  
-   パスが有効 (<xref:System.IO.DirectoryNotFoundException>クラス)。  
  
-   パスがコロンにのみ、":"(<xref:System.NotSupportedException>クラス)。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 ファイル名からファイルの内容を判断しないでください。 たとえば、`Form1.vb` というファイルは Visual Basic のソース ファイルではない可能性もあります。 アプリケーションでデータを使用する前に、入力をすべて検証してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Media.SoundPlayer>   
 [方法: Windows フォーム内で非同期的にサウンドを読み込む](../../../../docs/framework/winforms/controls/how-to-load-a-sound-asynchronously-within-a-windows-form.md)   
 