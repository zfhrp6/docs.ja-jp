---
title: "How to: Read a Value from a Registry Key in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "registry keys, determining if a value exists in"
  - "My.Computer.Registry object, examples"
  - "registry, determining if values exist"
  - "registry keys, reading from"
  - "registry, reading"
ms.assetid: 775d0a57-68c9-464e-8949-9a39bd29cc64
caps.latest.revision: 31
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 31
---
# How to: Read a Value from a Registry Key in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`My.Computer.Registry` オブジェクトの `GetValue` メソッドを使用すると、Windows レジストリ内の値を読み取ることができます。  
  
 キーが、次の例の 「Software \\MyApp」）が存在しないと、例外がスローされます。  `ValueName`が、次の例の 「名前」）が存在しないと、 `Nothing` が返されます。  
  
 また `GetValue` のメソッドが指定された値が特定のレジストリ キーにあるかどうかを確認するために使用できます。  
  
 コードを Web アプリケーションからレジストリを読み取る場合、現在のユーザーは、 Web アプリケーションで実装されている認証と偽装によって決まります。  
  
### レジストリ キーの値を読み取るには  
  
-   `GetValue` メソッドをパスと名前を指定して使用し、レジストリ キーから値を読み取ります。  次の例では、`HKEY_CURRENT_USER\Software\MyApp` から値 `Name` を読み取り、メッセージ ボックスにこの値を表示します。  
  
     [!code-vb[VbResourceTasks#4](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-read-a-value-from_1.vb)]  
  
 このコードの例は、IntelliSense コード スニペットとしても利用できます。  コード スニペット ピッカーでは、これは **\[Windows オペレーティング システム \> Registry\]** にあります。  詳細については、「[コード スニペット](/visual-studio/ide/code-snippets)」を参照してください。  
  
### レジストリ キーに値が存在するかどうかを確認するには  
  
-   `GetValue` メソッドを使用して、値を取得します。  値があり、メッセージを返すかどうかを、次のコードをチェックします。  
  
     [!code-vb[VbResourceTasks#12](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/visualbasic/how-to-read-a-value-from_2.vb)]  
  
## 信頼性の高いプログラミング  
 レジストリには、データを格納するために使用されるキーが、最上位またはルートに保持されます。  たとえば、HKEY\_LOCAL\_MACHINE ルート キーは、すべてのユーザーに使用されるマシン レベルの設定を格納するために使用されます。HKEY\_CURRENT\_USER は、個々のユーザー固有のデータを格納するために使用されます。  
  
 次の条件を満たす場合は、例外が発生する可能性があります。  
  
-   キーの名前が `Nothing` \(<xref:System.ArgumentNullException>\) である場合。  
  
-   ユーザーにレジストリ キーを読み取る権限が与えられていない場合 \(<xref:System.Security.SecurityException>\)  
  
-   キー名が 255 文字の制限を超えている場合 \(<xref:System.ArgumentException>\)  
  
## .NET Framework セキュリティ  
 このプロセスを実行するには、アセンブリに対して <xref:System.Security.Permissions.RegistryPermission> クラスで権限レベルが許可されている必要があります。  完全には信頼できないコンテキストでプロセスを実行している場合は、権限不足のため例外がスローされることがあります。  同様に、設定の作成または書き込みを行うために、ユーザーは正しい ACL を持っている必要があります。  たとえば、コード アクセス セキュリティ権限のあるローカル アプリケーションに、オペレーティング システム権限があるとは限りません。  詳細については、「[コード アクセス セキュリティの基礎](../Topic/Code%20Access%20Security%20Basics.md)」を参照してください。  
  
## 参照  
 <xref:Microsoft.VisualBasic.MyServices.RegistryProxy>   
 <xref:Microsoft.Win32.RegistryHive>   
 [Reading from and Writing to the Registry](../../../../visual-basic/developing-apps/programming/computer-resources/reading-from-and-writing-to-the-registry.md)