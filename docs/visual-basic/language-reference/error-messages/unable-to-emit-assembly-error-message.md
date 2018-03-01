---
title: "アセンブリを作成できません:&lt;エラー メッセージ&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b19b6439d85822c69adac0b3e0e04b2f31299836
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>アセンブリを作成できません:&lt;エラー メッセージ&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラは、マニフェストを伴うアセンブリを生成するためにアセンブリ リンカー (Al.exe、Alink とも呼ばれます) を呼び出しますが、アセンブリを生成する出力段階でリンカーからエラーが報告されます。  
  
 **エラー ID:** BC30145  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、トピックを参照して[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)です。 さらに詳しい説明とアドバイスを参照します。  
  
2.  アセンブリに手動で署名するかを使用して再試行してください、 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)または[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)です。  
  
3.  エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。  
  
### <a name="to-sign-the-assembly-manually"></a>アセンブリを手動で署名するには  
  
1.  [Sn.exe (厳密名ツール)] を使用して[Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md)) 公開/秘密キー ペア ファイルを作成します。  
  
     このファイルは .snk の拡張子を持ちます。  
  
2.  エラーが発生している COM 参照をプロジェクトから削除します。  
  
3.  Windows から**開始** メニューのをポイント**プログラム**、 をポイント**Microsoft Visual Studio 2008**、 をポイント**Visual Studio Tools**、およびをクリックして**Visual Studio 2008 コマンド プロンプト**です。  
  
4.  アセンブリ ラッパーを格納するディレクトリに移動します。  
  
5.  次のコードを入力します。  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     コードの一例として、次のように入力することができます。  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     パスやファイルに空白が含まれている場合には、二重引用符 (") を使用します。  
  
6.  [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] で、作成したファイルに .NET アセンブリへの参照を追加します。  
  
## <a name="see-also"></a>参照  
 
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)です。  
 [Sn.exe (厳密名ツール)][Sn.exe (厳密名ツール)](../../../framework/tools/sn-exe-strong-name-tool.md))  
 [方法: 公開キーと秘密キーのキー ペアを作成する](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [ご意見](/visualstudio/ide/talk-to-us)
