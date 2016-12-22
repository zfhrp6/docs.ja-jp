---
title: "/errorreport (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/errorreport"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "-errorreport compiler option [C#]"
  - "errorreport compiler option [C#]"
  - "/errorreport compiler option [C#]"
ms.assetid: bd0e7493-b79d-4369-9c3f-ba26ebdfbedf
caps.latest.revision: 35
caps.handback.revision: 35
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /errorreport (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

このオプションは、C\# 内部コンパイル エラーを Microsoft に報告するときの便利な方法として機能します。  
  
> [!NOTE]
>  Windows Vista および Windows Server 2008 では、Visual Studio のエラー レポート設定によって、Windows Error Reporting \(WER\) 経由で行った設定がオーバーライドされることはありません。  WER 設定は、常に Visual Studio エラー レポート設定よりも優先されます。  
  
## 構文  
  
```  
/errorreport:{ none | prompt | queue | send }  
```  
  
## Arguments  
 **none**  
 内部コンパイラ エラーを収集しない、またはマイクロソフトに送信しないことを報告します。  
  
 **prompt**  
 内部コンパイラ エラーを受信したときにレポートを送信するようにプロンプトを表示します。  **prompt** は、開発環境でアプリケーションをコンパイルする場合の既定値です。  
  
 **queue**  
 エラー レポートをキューに配置します。  管理者資格情報を使用してログオンすると、前回のログオン以降に発生したすべてのエラーを報告できます。  エラー レポートを送信するためのダイアログ ボックスが表示されるのは、3 日に 1 度だけです。  **queue** は、コマンド ラインでアプリケーションをコンパイルする場合の既定値です。  
  
 **send**  
 内部コンパイラ エラーのレポートをマイクロソフトに自動的に送信します。  このオプションを有効にするには、まずマイクロソフトのデータ収集ポリシーに同意する必要があります。  コンピューターで **\/errorreport:send** を初めて指定すると、マイクロソフトのデータ収集ポリシーが記載されている Web サイトが表示されます。  
  
 このオプションは、レジストリの設定によって異なります。  レジストリに適切な値を設定する方法の詳細については、MSDN Web サイトの [Visual Studio 2008 コマンド ライン ツールの自動エラー レポートを表示する方法](http://go.microsoft.com/fwlink/?LinkID=184695) "参照してください。  
  
## 解説  
 コンパイラがソース コード ファイルを処理できないと、内部コンパイラ エラー \(ICE: Internal Compiler Error\) が発生します。  ICE が発生した場合は、コードの修正に利用できる出力ファイルや診断は生成されません。  
  
 以前のリリースでは、ICE が発生した場合はマイクロソフト プロダクト サポート サービスに連絡して問題を報告することをお勧めしていました。  **\/errorreport** を使用すると、ICE 情報を Visual C\# チームに提供できます。  エラー レポートは、今後リリースされるコンパイラの機能向上に役立ちます。  
  
 ユーザーが使用できるレポート送信機能は、使用しているコンピューターやユーザー ポリシーのアクセス許可に応じて異なります。  
  
 エラー デバッガーの詳細については、参照します [Windows \(Drwatson.exe\) ツール ツール用"ワトソン説明](http://go.microsoft.com/fwlink/?LinkId=147286)。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  詳細については、「[\[ビルド\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Build%20Page,%20Project%20Designer%20\(C%23\).md)」を参照してください。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  \[詳細設定\] ボタンをクリックします。  
  
4.  **\[内部コンパイル エラー報告\]** プロパティを変更します。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.ErrorReport%2A>」を参照してください。  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)