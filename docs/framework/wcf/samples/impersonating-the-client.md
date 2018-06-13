---
title: クライアントの偽装
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, impersonation sample
- Impersonating the Client Sample [Windows Communication Foundation]
- impersonation, Windows Communication Foundation sample
ms.assetid: 8bd974e1-90db-4152-95a3-1d4b1a7734f8
ms.openlocfilehash: 4c5d911bfbfcd33248e15b9fc822abdc9cf4046c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505011"
---
# <a name="impersonating-the-client"></a>クライアントの偽装
偽装のサンプルでは、サービスで呼び出し元のアプリケーションを偽装し、サービスが呼び出し元の代わりにシステム リソースにアクセスできるようにする方法を示します。  
  
 このサンプルがに基づいて、[自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)サンプルです。 同じサービスとクライアントの構成ファイルは、[自己ホスト](../../../../docs/framework/wcf/samples/self-host.md)サンプルです。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 サービス コードは、サービスの `Add` メソッドが <xref:System.ServiceModel.OperationBehaviorAttribute> を使用して呼び出し元を偽装するように変更されています。次のサンプル コードを参照してください。  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    Console.WriteLine("Received Add({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
    DisplayIdentityInformation();  
    return result;  
}  
```  
  
 この結果、実行中のスレッドのセキュリティ コンテキストは呼び出し元を偽装するように切り替えられ、その後 `Add` メソッドが入力されて、このメソッドが終了すると元に戻ります。  
  
 次のサンプル コードに示す `DisplayIdentityInformation` メソッドは、呼び出し元の ID を表示するユーティリティ関数です。  
  
```  
static void DisplayIdentityInformation()  
{  
    Console.WriteLine("\t\tThread Identity            :{0}",  
         WindowsIdentity.GetCurrent().Name);  
    Console.WriteLine("\t\tThread Identity level  :{0}",   
         WindowsIdentity.GetCurrent().ImpersonationLevel);  
    Console.WriteLine("\t\thToken                     :{0}",  
         WindowsIdentity.GetCurrent().Token.ToString());  
    return;  
}  
```  
  
 サービスの `Subtract` メソッドは、強制呼び出しを使用して呼び出し元を偽装します。次のサンプル コードを参照してください。  
  
```  
public double Subtract(double n1, double n2)  
{  
    double result = n1 - n2;  
    Console.WriteLine("Received Subtract({0},{1})", n1, n2);  
    Console.WriteLine("Return: {0}", result);  
Console.WriteLine("Before impersonating");  
DisplayIdentityInformation();  
  
    if (ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Impersonation ||  
        ServiceSecurityContext.Current.WindowsIdentity.ImpersonationLevel == TokenImpersonationLevel.Delegation)  
    {  
        // Impersonate.  
        using (ServiceSecurityContext.Current.WindowsIdentity.Impersonate())  
        {  
            // Make a system call in the caller's context and ACLs   
            // on the system resource are enforced in the caller's context.   
            Console.WriteLine("Impersonating the caller imperatively");  
            DisplayIdentityInformation();  
        }  
    }  
    else  
    {  
        Console.WriteLine("ImpersonationLevel is not high enough to perform this operation.");  
    }  
  
Console.WriteLine("After reverting");  
DisplayIdentityInformation();  
    return result;  
}  
```  
  
 この場合、呼び出し元は呼び出し全体に対して偽装されるのではなく、呼び出しの一部に対してのみ偽装されます。 通常、操作全体の偽装を行うよりも、最小限の範囲での偽装をお勧めします。  
  
 他のメソッドは呼び出し元を偽装しません。  
  
 クライアント コードは、偽装レベルを <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> に設定するように変更されています。 クライアントは <xref:System.Security.Principal.TokenImpersonationLevel> 列挙体を使用して、サービスで使用される偽装レベルを指定します。 この列挙体は、<xref:System.Security.Principal.TokenImpersonationLevel.None>、<xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>、<xref:System.Security.Principal.TokenImpersonationLevel.Identification>、<xref:System.Security.Principal.TokenImpersonationLevel.Impersonation>、および <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> の値をサポートします。 Windows ACL を使用して保護されているローカル コンピューターのシステム リソースにアクセスする場合、アクセス チェックを実行するには、偽装レベルを <xref:System.Security.Principal.TokenImpersonationLevel.Impersonation> に設定する必要があります。次のサンプル コードを参照してください。  
  
```  
// Create a client with given client endpoint configuration  
CalculatorClient client = new CalculatorClient();  
  
client.ClientCredentials.Windows.AllowedImpersonationLevel = TokenImpersonationLevel.Impersonation;  
```  
  
 このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。 どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。  
  
> [!NOTE]
>  サービスの管理者アカウントで実行する必要がありますまたはそれを実行するアカウントに登録する権限を与える必要があります、 http://localhost:8000/ServiceModelSamples HTTP レイヤーを使用して URI。 設定して、そのような権利を与えることができます、 [Namespace 予約](http://go.microsoft.com/fwlink/?LinkId=95012)を使用して、 [Httpcfg.exe ツール](http://go.microsoft.com/fwlink/?LinkId=95010)です。  
  
> [!NOTE]
>  [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] を実行しているコンピューターでは、Host.exe アプリケーションに偽装特権がある場合にのみ偽装がサポートされます  (既定では、管理者のみがこれを許可できます)。サービスを実行しているアカウントにこの特権を追加するに移動**管理ツール**、開かれている**ローカル セキュリティ ポリシー**、開かれている**ローカル ポリシー**をクリックして**ユーザー権利の割り当て**を選択して**認証後にクライアントを偽装** をダブルクリック**プロパティ**ユーザーまたはグループに追加します。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
3.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
4.  サービスが呼び出し元を偽装していることを示すため、サービスが実行されているアカウントとは異なるアカウントでクライアントを実行します。 これを行うには、コマンド プロンプトに次のコマンドを入力します。  
  
    ```  
    runas /user:<machine-name>\<user-name> client.exe  
    ```  
  
     次に、パスワードの入力が求められます。 先ほど指定したアカウントのパスワードを入力します。  
  
5.  クライアントを実行する際、クライアントを実行する前と後で ID の資格情報が異なることに注意してください。  
  
## <a name="see-also"></a>関連項目
