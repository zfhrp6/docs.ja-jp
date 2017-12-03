---
title: "方法: WCF URL 予約を制限付きの予約に置き換える"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2754d223-79fc-4e2b-a6ce-989889f2abfa
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8c25403f298444732f6787979add595bd877bb2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation"></a>方法: WCF URL 予約を制限付きの予約に置き換える
URL 予約を使用すると、特定の URL または URL セットからメッセージを受信するユーザーを制限できます。 予約は、URL テンプレート、アクセス制御リスト (ACL)、およびフラグのセットで構成されます。 URL テンプレートは、予約の対象となる URL を定義します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]URL テンプレートが処理される方法を参照してください。[着信要求のルーティング](http://go.microsoft.com/fwlink/?LinkId=136764)です。 ACL は、指定された URL からメッセージを受信できるユーザーまたはユーザー グループを制御します。 フラグは、その予約で、ユーザーまたはグループに URL を直接リッスンする権限を与えるか、リッスンを他のプロセスに委任する権限を与えるかを指定します。  
  
 既定のオペレーティング システム構成の一部として、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] はポート 80 に対してグローバルにアクセス可能な予約を作成します。これにより、すべてのユーザーは、双方向通信にデュアル HTTP バインディングを使用するアプリケーションを実行できます。 この予約の ACL はすべてのユーザー向けなので、管理者は URL または URL セットをリッスンする権限を明示的に許可または拒否することはできません。 このトピックでは、この予約を削除し、制限された ACL を使用する予約を再作成する方法について説明します。  
  
 [!INCLUDE[wv](../../../../includes/wv-md.md)] または [!INCLUDE[lserver](../../../../includes/lserver-md.md)] では、管理特権でのコマンド プロンプトから「`netsh http show urlacl`」と入力することで、すべての HTTP URL 予約を表示できます。  次に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] URL 予約の例を示します。  
  
```  
Reserved URL : http://+:80/Temporary_Listen_Addresses/  
        User: \Everyone  
            Listen: Yes  
            Delegate: No  
            SDDL: D:(A;;GX;;;WD)  
```  
  
 この予約には、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションが双方向通信にデュアル HTTP バインディングを使用する際の URL テンプレートが含まれています。 この形式の URL は、デュアル HTTP バインディングを介して通信する際に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントにメッセージを返信するために使用されます。 すべてのユーザーに対して、URL をリッスンする権限が与えられていますが、リッスンを他のプロセスに委任する権限は与えられていません。 また、ACL は SSDL (Security Descriptor Definition Language) で記述されています。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]SSDL を参照してください[SSDL](http://go.microsoft.com/fwlink/?LinkId=136789)  
  
### <a name="to-delete-the-wcf-url-reservation"></a>WCF URL 予約を削除するには  
  
1.  をクリックして**開始**、 をポイント**すべてのプログラム**、 をクリックして**アクセサリ**を右クリックして**コマンド プロンプト** をクリック**として実行管理者**されるコンテキスト メニューの します。 をクリックして**続行**ウィンドウで、ユーザー アカウント制御 (UAC) された続行するアクセス許可を要求する可能性があります。  
  
2.  入力**netsh http 削除 urlacl url = http://+:80/Temporary_Listen_Addresses/**コマンド プロンプト ウィンドウで。  
  
3.  予約が正常に削除されると、次のメッセージが表示されます。 **URL 予約が正常に削除されました**  
  
## <a name="creating-a-new-security-group-and-new-restricted-url-reservation"></a>新しいセキュリティ グループおよび新しい制限付き URL 予約の作成  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] URL 予約を制限付きの予約に置き換えるには、まず新しいセキュリティ グループを作成する必要があります。 この操作は、コマンド プロンプトを使用する方法か、コンピューターの管理コンソールを使用する方法で行うことができます。 行う必要があるのはいずれか一方のみです。  
  
#### <a name="to-create-a-new-security-group-from-a-command-prompt"></a>コマンド プロンプトで新しいセキュリティ グループを作成するには  
  
1.  をクリックして**開始**、 をポイント**すべてのプログラム**、 をクリックして**アクセサリ**を右クリックして**コマンド プロンプト** をクリック**として実行管理者**されるコンテキスト メニューの します。 をクリックして**続行**ウィンドウで、ユーザー アカウント制御 (UAC) された続行するアクセス許可を要求する可能性があります。  
  
2.  入力**net localgroup"\<セキュリティ グループ名 >"/コメント:"\<セキュリティ グループの説明 >"を追加/**コマンド プロンプトでします。 置き換える**\<セキュリティ グループ名 >**を作成するセキュリティ グループの名前と**\<セキュリティ グループの説明 >**の適切な説明と、セキュリティ グループ。  
  
3.  セキュリティ グループが正常に作成されると、次のメッセージが表示されます。 **コマンドが正常に完了しました。**  
  
#### <a name="to-create-a-new-security-group-from-the-computer-management-console"></a>コンピューターの管理コンソールで新しいセキュリティ グループを作成するには  
  
1.  をクリックして**開始**、 をクリックして**コントロール パネルの** 、 をクリックして**管理ツール**、 をクリック**コンピューターの管理**を開くには、コンピューターを管理コンソールです。 をクリックして**続行**ウィンドウで、ユーザー アカウント制御 (UAC) された続行するアクセス許可を要求する可能性があります。  
  
2.  をクリックして**システム ツール**、 をクリックして**ローカル ユーザーとグループ**を右クリックして**グループ**フォルダーをクリック**新規グループ**コンテキスト メニューを取得します。 入力**グループ名**、**説明**およびその他の詳細をクリックしてこの新しいセキュリティ グループの**作成**セキュリティ グループを作成するボタンをクリックします。  
  
#### <a name="to-create-the-restricted-url-reservation"></a>制限付き URL 予約を作成するには  
  
1.  をクリックして**開始**、 をポイント**すべてのプログラム**、 をクリックして**アクセサリ**を右クリックして**コマンド プロンプト** をクリック**として実行管理者**されるコンテキスト メニューの します。 をクリックして**続行**ウィンドウで、ユーザー アカウント制御 (UAC) された続行するアクセス許可を要求する可能性があります。  
  
2.  入力**netsh http 追加 urlacl url = http://+: 80/Temporary_Listen_Addresses/ユーザー ="\<マシン名 >\\< セキュリティ グループ名\>**コマンド プロンプトで。 置き換える**\<マシン名 >**をコンピューター名、グループを作成する必要がありますと**\<セキュリティ グループ名 >**を作成したセキュリティ グループの名前先に。  
  
3.  予約が正常に作成されると、 **URL 予約が正常に追加された**です。
