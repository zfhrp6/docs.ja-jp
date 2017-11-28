---
title: "アセンブリ マニフェストを作成中にエラー:&lt;エラー メッセージ&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords: BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d846ef88f0c36b49e79b9d11252fcef419dfa0ee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>アセンブリ マニフェストを作成中にエラー:&lt;エラー メッセージ&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] コンパイラはアセンブリ リンカー (Al.exe、Alink とも呼ばれる) を呼び出し、マニフェストを伴うアセンブリを生成します。 リンカーが、アセンブリの生成前の段階でのエラーを報告しています。  
  
 指定したキー ファイルまたはキー コンテナーに原因がある場合があります。 アセンブリに完全署名するには、公開キーと秘密キーに関する情報を含む有効なキー ファイルを提供する必要があります。 アセンブリに遅延署名するには、**[遅延署名のみ]** チェック ボックスをオンにし、公開キー情報を含む有効なキー ファイルを提供する必要があります。 アセンブリに遅延署名する場合、秘密キーは必要ありません。 詳細については、次を参照してください。[する方法: アセンブリ (Visual Studio) に署名](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)です。  
  
 **エラー ID:** BC30140  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、トピックを参照して[Al.exe ツールのエラーと警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)エラー AL1019 の説明とアドバイスをさらに  
  
2.  エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。  
  
## <a name="see-also"></a>関連項目  
 [方法: アセンブリに署名する (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)  
 [[署名] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/signing-page-project-designer)  
 [Al.exe (アセンブリ リンカー)](https://msdn.microsoft.com/library/c405shex)  
 [Al.exe ツールのエラーと警告](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [ご意見](/visualstudio/ide/talk-to-us)
