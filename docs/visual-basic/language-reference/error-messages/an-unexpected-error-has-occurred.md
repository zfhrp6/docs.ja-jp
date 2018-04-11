---
title: 単一インスタンスのスタートアップに必要なオペレーティング システムのリソースが取得できないため、予期しないエラーが発生しました。
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrAppModel_CantGetMemoryMappedFile
ms.assetid: 0d9f2a30-ff72-4355-8060-744f22339359
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8969303d66e946d5579c6cca592b5701c4ebd632
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="an-unexpected-error-has-occurred-because-an-operating-system-resource-required-for-single-instance-startup-cannot-be-acquired"></a>単一インスタンスのスタートアップに必要なオペレーティング システムのリソースが取得できないため、予期しないエラーが発生しました。
アプリケーションは、必要なオペレーティング システムのリソースを取得できませんでした。 この問題の考えられる原因の一部は次のとおりです。  
  
-   指定されたオペレーティング システム オブジェクトを作成するためのアクセス許可がアプリケーションにない。  
  
-   メモリ マップト ファイルを作成するためのアクセス許可が共通言語ランタイムにない。  
  
-   アプリケーションからオペレーティング システム オブジェクトにアクセスする必要があるが、別のプロセスがそれを使用している。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  指定されたオペレーティング システム オブジェクトを作成するための十分なアクセス許可がアプリケーションにあることを確認します。  
  
2.  メモリ マップト ファイルを作成するための十分なアクセス許可が共通言語ランタイムにあることを確認します。  
  
3.  コンピューターを再起動して、元のインスタンス アプリケーションへの接続に必要なリソースを使用している可能性のあるプロセスをすべて削除します。  
  
4.  エラーが発生した状況を記録して、マイクロソフト プロダクト サポート サービスにご連絡ください。  
  
## <a name="see-also"></a>関連項目  
 [[アプリケーション] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/application-page-project-designer-visual-basic)  
 [デバッガーの基本事項](/visualstudio/debugger/debugger-basics)  
 [ご意見](/visualstudio/ide/talk-to-us)
