---
title: "内部エラーのために完全な運用システム名を取得できませんでした"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e90de5a2fd0699a449e05b9c32e7450b8bdc991
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a>内部エラーのために完全な運用システム名を取得できませんでした
内部エラーのために完全な運用システム名を取得できませんでした。 これは、現在のコンピューターに WMI が存在しないことが原因である場合があります。  
  
 `My.Computer.Info.OSFullName` プロパティの呼び出しに失敗しました。 このエラーの考えられる原因は、Windows Management Instrumentation (WMI) が、現在のコンピューターにインストールされていないことです。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  `Try...Catch` プロパティの呼び出しの周囲に `My.Computer.Info.OSFullName` ブロックを追加します。  
  
2.  WMI およびそのインストール方法の詳細については、「Windows Management Instrumentation Core」を検索してに移動します。  
  
## <a name="see-also"></a>参照  
 [My.Computer.Info.OSFullName](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [例外と Visual Basic でのエラー処理](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [Try...Catch...Finally ステートメント](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
