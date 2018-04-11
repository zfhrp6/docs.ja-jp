---
title: スタートアップ フォームが指定されていません。
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_NoStartupForm
ms.assetid: 8e04af49-4bef-49de-a7ec-e407e9873da7
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fdffc182ee66497d68aafb7dc37cfef75b4d2e9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="a-startup-form-has-not-been-specified"></a>スタートアップ フォームが指定されていません。
アプリケーションを使用して、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>クラスが、スタートアップ フォームが指定されていません。  
  
 これは、場合に発生することができます、**有効にするアプリケーション フレームワーク**プロジェクト デザイナー チェック ボックスが選択されているが、**スタートアップ フォーム**が指定されていません。 詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  アプリケーションのスタートアップ オブジェクトを指定します。  
  
     詳細については、「[[アプリケーション] ページ (プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
2.  上書き、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>を設定するメソッド、<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>スタートアップ フォームにプロパティです。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OnCreateMainForm%2A>  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.MainForm%2A>  
 [Visual Basic アプリケーション モデルの概要](../../../visual-basic/developing-apps/development-with-my/overview-of-the-visual-basic-application-model.md)
