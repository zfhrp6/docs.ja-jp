---
title: アセンブリ マニフェストを作成中にエラー:&lt;エラー メッセージ&gt;
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4032bbcbf9924eb5aad4e2cb1a6e74df9a472eca
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>アセンブリ マニフェストを作成中にエラー:&lt;エラー メッセージ&gt;
Visual Basic コンパイラは、マニフェストを伴うアセンブリを生成するアセンブリ リンカー (Al.exe、Alink とも呼ばれます) を呼び出します。 リンカーが、アセンブリの生成前の段階でのエラーを報告しています。  
  
 指定したキー ファイルまたはキー コンテナーに原因がある場合があります。 アセンブリに完全署名するには、公開キーと秘密キーに関する情報を含む有効なキー ファイルを提供する必要があります。 アセンブリに遅延署名するには、**[遅延署名のみ]** チェック ボックスをオンにし、公開キー情報を含む有効なキー ファイルを提供する必要があります。 アセンブリに遅延署名する場合、秘密キーは必要ありません。 詳しくは、「[方法 : 厳密な名前でアセンブリに署名する](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)」をご覧ください。  
  
 **エラー ID:** BC30140  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  引用符で囲まれたエラー メッセージを確認し、トピックを参照して[Al.exe](../../../framework/tools/al-exe-assembly-linker.md)です。 エラー AL1019 説明とアドバイスを参照  
  
2.  エラーが続く場合は、状況に関する情報を収集し、マイクロソフト プロダクト サポート サービスに通知してください。  
  
## <a name="see-also"></a>関連項目  
 [方法: 厳密な名前でアセンブリに署名する](../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [[署名] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/signing-page-project-designer)  
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)です。  
 [ご意見](/visualstudio/ide/talk-to-us)
