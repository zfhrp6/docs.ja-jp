---
title: "この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrAppModel_SingleInstanceCantConnect
ms.assetid: 7c2c0cee-02a1-4157-be03-39d18e18408f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fbc8458231c36f3af9ca4de524e01e19a162ee47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="this-single-instance-application-could-not-connect-to-the-original-instance"></a>この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした
この単一インスタンス アプリケーションは元のインスタンスに接続できませんでした。 この問題の考えられる原因の一部は次のとおりです。  
  
-   元のインスタンスが応答を停止した。  
  
-   カーネル オブジェクトを作成するためのアクセス許可がアプリケーションにない。 カーネル オブジェクトの詳細については、次を参照してください。[ミュー テックス](../../standard/threading/mutexes.md)です。  
  
     カーネル オブジェクトの基本名は、アセンブリの GUID、メジャー バージョン番号、およびマイナー バージョン番号を連結したものです。 たとえば、基本名が `3639f15d-9547-43da-8145-60da347829915.1`になる可能性があります。  
  
## <a name="to-correct-this-error-when-developing-the-application"></a>アプリケーションを開発しているときに、このエラーを解決するには  
  
1.  アプリケーションが応答していない状態にならないことを確認します。  
  
2.  カーネル オブジェクトを作成するための十分なアクセス許可がアプリケーションにあることを確認します。  
  
3.  アプリケーションの元のインスタンスを再起動します。  
  
4.  コンピューターを再起動して、元のインスタンス アプリケーションへの接続に必要なリソースを使用している可能性のあるプロセスをすべて削除します。  
  
5.  エラーが発生した状況を記録して、Microsoft 製品サポート サービスに電話でご連絡ください。  
  
## <a name="see-also"></a>関連項目  
 [NIB: 方法: アプリケーション (Visual Basic) のインスタンス化動作を指定します。](http://msdn.microsoft.com/en-us/48539ad8-d960-4210-beab-ee65f6c6dc6e)  
 [デバッガーの基本事項](/visualstudio/debugger/debugger-basics)  
 [PAVEOVER 製品のサポートとアクセシビリティ](http://msdn.microsoft.com/en-us/14e1d293-7b6d-40a6-bf3e-a92f8ee6c88c)
