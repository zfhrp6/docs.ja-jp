---
title: "方法 : Visual Studio のコマンドラインのための環境変数を設定する"
ms.date: 09-29-2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8012e310bb04ec3acef0790f9cd50ed42dd9286a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>方法 : Visual Studio のコマンドラインのための環境変数を設定する

VsDevCmd.bat ファイルでは、コマンド ライン ビルドを有効にする適切な環境変数を設定します。 VsDevCmd.bat の詳細については、次を参照してください。[サポート技術情報の記事 Q248802](http://go.microsoft.com/fwlink/?LinkId=225042)です。  

> [!NOTE]
> VsDevCmd.bat ファイルは、Visual Studio 2017 で提供される新しいファイルです。 Visual Studio 2015 と以前のバージョンは、VSVARS32.bat を同じ目的で使用されます。 \Program Files\Microsoft Visual Studio でこのファイルが格納されている\\*バージョン*\Common7\Tools または Program Files (x86) \Microsoft Visual Studio\\*バージョン*\Common7\Tools です。
  
Visual Studio の現在のバージョンが Visual Studio の以前のバージョンは、コンピューターにインストールされている場合は、VsDevCmd.bat と VSVARS32 を実行する必要がありますされません。同じコマンド プロンプト ウィンドウで異なるバージョンの BAT です。 代わりに、独自のウィンドウで、各バージョンのコマンドを実行する必要があります。
  
### <a name="to-run-vsdevcmdbat"></a>VsDevCmd.BAT を実行するには  
  
1.  **開始**メニューを開き、 **VS 2017 用開発者コマンド プロンプト**です。  内にある、 **Visual Studio 2017**フォルダーです。
  
2.  \Program Files\Microsoft Visual Studio に変更\\*バージョン*\\*内容*\Common7\Tools または \Program Files (x86) \Microsoft Visual Studio\\*バージョン*\\*内容*インストールの \Common7\Tools サブディレクトリです。  (*バージョン*は*2017*現在のバージョン。 *提供*の 1 つ*エンタープライズ*、 *Professional*または*コミュニティ*)。
  
3.  VsDevCmd.bat を入力して実行**VsDevCmd**です。  
  
    > [!CAUTION]
    >  VsDevCmd.bat には、コンピューターを変更できます。 欠落または破損して VsDevCmd.bat ファイルを別のコンピューターから VsDevCmd.bat と置き換えないでください。 その場合は、セットアップ プログラムを再実行してファイルを置き換えてください。  
  
## <a name="see-also"></a>関連項目  
 [csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
