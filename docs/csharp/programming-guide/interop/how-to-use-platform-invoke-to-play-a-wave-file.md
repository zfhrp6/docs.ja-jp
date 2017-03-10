---
title: "方法: プラットフォーム呼び出しを使用して Wave ファイルを再生する (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ".wav ファイル"
  - "相互運用性 [C#], pinvoke による WAV ファイルの再生"
  - "プラットフォーム呼び出し, サウンド ファイル"
  - "wav ファイル"
ms.assetid: f7f62f53-e026-4c40-b221-3a26adb0c2c5
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# 方法: プラットフォーム呼び出しを使用して Wave ファイルを再生する (C# プログラミング ガイド)
次の C\# のコード例は、プラットフォーム呼び出しサービスを利用して、Windows オペレーティング システムで Wave サウンド ファイルを再生する方法を示しています。  
  
## 使用例  
 このコード例では、`DllImport` を使用して、`winmm.dll` の `PlaySound` メソッド エントリ ポイントを `Form1 PlaySound()` としてインポートします。  この例には、ボタン付きの簡単な Windows フォームがあります。  ボタンをクリックすると、標準の Windows <xref:System.Windows.Forms.OpenFileDialog> ダイアログ ボックスが表示され、再生するファイルを開くことができます。  Wave ファイルを選択すると、winmm.DLL アセンブリ メソッドの `PlaySound()` メソッドを使ってファイルが再生されます。  winmm.DLL の `PlaySound` メソッドの詳細については、「[Using the PlaySound function with Waveform\-Audio Files \(PlaySound 関数と WAVE 形式オーディオ ファイルの使用\)](http://go.microsoft.com/fwlink/?LinkId=148553)」を参照してください。  .wav 拡張子を持つファイルを参照して選択します。**\[開く\]** をクリックし、プラットフォーム呼び出しを使って Wave ファイルを再生します。  選択したファイルの完全パスがテキスト ボックスに表示されます。  
  
 **\[開いているファイル\]** ダイアログ ボックスには、フィルター設定に従って .wav 拡張子を持つファイルだけが表示されます。  
  
 [!code-cs[csProgGuideInterop#5](../../../csharp/programming-guide/interop/codesnippet/csharp/how-to-use-platform-invo_1.cs)]  
  
 [!code-cs[csProgGuideInterop#3](../../../csharp/programming-guide/interop/codesnippet/csharp/how-to-use-platform-invo_2.cs)]  
  
## コードのコンパイル  
  
### コードをコンパイルするには  
  
1.  Visual Studio で、新しい C\# Windows アプリケーション プロジェクトを作成し、WinSound という名前を付けます。  
  
2.  上記のコードをコピーし、`Form1.cs` ファイルの内容に貼り付けます。  
  
3.  下記のコードをコピーし、`Form1.Designer.cs` ファイル内の `InitializeComponent()` メソッドの既存コードより後に貼り付けます。  
  
     [!code-cs[csProgGuideInterop#4](../../../csharp/programming-guide/interop/codesnippet/csharp/how-to-use-platform-invo_3.cs)]  
  
4.  コードをコンパイルして実行します。  
  
## .NET Framework セキュリティ  
 詳細については、「[.NET Framework Security](http://go.microsoft.com/fwlink/?LinkId=37122)」を参照してください。  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [相互運用性の概要](../../../csharp/programming-guide/interop/interoperability-overview.md)   
 [相互運用性の概要](../../../csharp/programming-guide/interop/interoperability-overview.md)   
 [A Closer Look at Platform Invoke](http://msdn.microsoft.com/ja-jp/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)   
 [プラットフォーム呼び出しによるデータのマーシャリング](../Topic/Marshaling%20Data%20with%20Platform%20Invoke.md)