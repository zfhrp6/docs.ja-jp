---
title: "EventLogSource で指定したソース名は、EventLogName で指定したログ以外のログに登録されています"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 7317e100-098b-408d-86e5-7c74cf8558c7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0a100789486dda403f483489e73accbf219374c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="source-name-specified-in-eventlogsource-is-registered-to-a-log-other-than-that-specified-in-eventlogname"></a>EventLogSource で指定したソース名は、EventLogName で指定したログ以外のログに登録されています
`EventLog` が、別のログに登録されているソースを参照しようとしています。 イベント ログにエントリを書き込んでいる場合は、 <xref:System.Diagnostics.EventLog.Source%2A> プロパティを指定する必要があります。 <xref:System.Diagnostics.EventLog.Source%2A> プロパティはコンポーネントを有効なエントリのソースとしてイベント ログに登録します。 1 つのソースは一度に 1 つのイベント ログにのみ関連付ける (つまり、エントリを書き込む) ことができます。  
  
 既定では、先にコンポーネントを有効なソースとして登録しないでエントリを書き込もうとした場合、 <xref:System.Diagnostics.EventLog.Source%2A> プロパティの値をソース文字列として使用して、自動的にソースがイベント ログに登録されます。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   ソースが、正しいログに登録されていることを確認します。 これを行うには、 <xref:System.Diagnostics.EventLog.CreateEventSource%2A> メソッドまたをそのオーバーロードのいずれかを使用して、コンポーネントを一意に識別する文字列をイベント ログに指定します。  
  
## <a name="see-also"></a>参照  
 [イベント ログの管理](http://msdn.microsoft.com/library/35f53238-bdd2-417b-acd8-2fd9f7397f18)  
 [イベント ログの参照](http://msdn.microsoft.com/library/4af0661c-6c96-49f4-961d-b26ed9bc3e87)  
 [方法: イベント ログ エントリのソースとして、アプリケーションを追加します。](http://msdn.microsoft.com/library/948ff920-a739-4e66-a191-ee951512d42c)  
 [方法: イベント ソースを削除](http://msdn.microsoft.com/library/bc66c900-4b8a-426a-b8e2-17031a20167e)
