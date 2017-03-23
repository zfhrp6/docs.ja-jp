---
title: "How to: Create a Registry Key and Set Its Value in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "RegistryKey.CreateSubKey"
  - "RegistryKey.SetValue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "registry keys, creating"
  - "registry, adding values"
  - "registry, adding keys"
  - "registry keys, setting values"
  - "examples [Visual Basic], registry"
ms.assetid: d3e40f74-c283-480c-ab18-e5e9052cd814
caps.latest.revision: 30
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 30
---
# How to: Create a Registry Key and Set Its Value in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Computer.Registry` オブジェクトの `CreateSubKey` メソッドを使用して、レジストリ キーを作成できます。  
  
## 手順  
  
#### レジストリ キーを作成するには  
  
-   `CreateSubKey` メソッドを使用して、キーを配置するハイブ、およびキーの名前を指定します。  パラメーター  `Subkey`  では、大文字と小文字は区別されません。  レジストリ キー `MyTestKey` を HKEY\_CURRENT\_USER の下に作成する例を次に示します。  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
#### レジストリ キーを作成し、値を設定するには  
  
1.  `CreateSubkey` メソッドを使用して、キーを配置するハイブ、およびキーの名前を指定します。  レジストリ キー `MyTestKey` を HKEY\_CURRENT\_USER の下に作成する例を次に示します。  
  
     [!code-vb[VbResourceTasks#17](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_1.vb)]  
  
2.  `SetValue` メソッドを使用して、値を設定します。  この例では、文字列値を次のように設定します。   "MyTestKeyValue" が "This is a test value" になります。  
  
     [!code-vb[VbResourceTasks#14](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_2.vb)]  
  
## 使用例  
 レジストリ キー `MyTestKey` を HKEY\_CURRENT\_USER の下に作成し、文字列値 `MyTestKeyValue` を `This is a test value` に設定する例を次に示します。  
  
 [!code-vb[VbResourceTasks#15](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-create-a-registry-key-and-set-its-value_3.vb)]  
  
## 信頼性の高いプログラミング  
 レジストリの構造を調べて、キーの適切な場所を見つけることができます。  たとえば、現在のユーザーの HKEY\_CURRENT\_USER\\Software key を開き、会社名を使用してキーを作成するとします。  その後で、会社名のキーにレジストリ値を追加します。  
  
 Web アプリケーションからレジストリを読み取る場合、現在のユーザーは、Web アプリケーションで実装されている認証と偽装によって異なります。  
  
 ローカル コンピューター \(<xref:Microsoft.Win32.Registry.LocalMachine>\) よりもユーザー フォルダー \(<xref:Microsoft.Win32.Registry.CurrentUser>\) にデータを書き込む方が安全です。  
  
 レジストリの値を作成するときは、その値が既存の値である場合の処理を決めておく必要があります。  悪意のあるユーザーによって作成された別のプロセスが既に値を作成し、アクセス権を持っている可能性があります。  レジストリ値にデータを設定すると、そのデータを他のプロセスから利用できるようになります。  これを回避するために、<xref:Microsoft.Win32.RegistryKey.GetValue%2A> メソッドを使用します。  このメソッドは、キーがまだ存在しない場合、`Nothing` を返します。  
  
 レジストリ キーがアクセス制御リスト \(ACL: Access Control List\) によって保護されている場合でも、パスワードなどの秘密のデータをプレーンテキストでレジストリに格納するのは危険です。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   キーの名前が `Nothing` \(<xref:System.ArgumentNullException>\) である場合。  
  
-   レジストリ キーを作成するためのアクセス許可がユーザーにない場合 \(<xref:System.Security.SecurityException>\)  
  
-   キー名が 255 文字の制限を超えている場合 \(<xref:System.ArgumentException>\)  
  
-   キーが閉じている場合 \(<xref:System.IO.IOException>\)  
  
-   レジストリ キーが読み取り専用の場合 \(<xref:System.UnauthorizedAccessException>\)  
  
## .NET Framework セキュリティ  
 このプロセスを実行するには、アセンブリに対して <xref:System.Security.Permissions.RegistryPermission> クラスで権限レベルが許可されている必要があります。  完全には信頼できないコンテキストでプロセスを実行している場合は、権限不足のため例外がスローされることがあります。  同様に、設定の作成または書き込みを行うために、ユーザーは正しい ACL を持っている必要があります。  たとえば、コード アクセス セキュリティ権限のあるローカル アプリケーションに、オペレーティング システム権限があるとは限りません。  詳細については、「[コード アクセス セキュリティの基礎](../Topic/Code%20Access%20Security%20Basics.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy.CurrentUser%2A>   
 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)   
 [コード アクセス セキュリティの基礎](../Topic/Code%20Access%20Security%20Basics.md)