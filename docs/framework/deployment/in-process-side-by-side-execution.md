---
title: "インプロセスの side-by-side 実行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "インプロセスの side-by-side 実行"
  - "side-by-side 実行, インプロセス"
ms.assetid: 18019342-a810-4986-8ec2-b933a17c2267
caps.latest.revision: 25
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 25
---
# インプロセスの side-by-side 実行
[!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、インプロセスの side\-by\-side ホスティングを使用して、1 つのプロセスで複数のバージョンの共通言語ランタイム \(CLR: Common Language Runtime\) を実行できます。  既定では、マネージ COM コンポーネントは、プロセスに読み込まれている .NET Framework のバージョンに関係なく、そのコンポーネントのビルドに使用された .NET Framework のバージョンで実行されます。  
  
## 背景  
 .NET Framework では、マネージ コード アプリケーションに対しては side\-by\-side ホスティングを常に提供してきましたが、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] まで、マネージ COM コンポーネントに対しては同様の機能がありませんでした。  これまで、プロセスに読み込まれたマネージ COM コンポーネントは、既に読み込まれているバージョンのランタイムか、インストールされている最新バージョンの .NET Framework で実行されていました。  このバージョンが COM コンポーネントと互換性がない場合、そのコンポーネントは失敗しました。  
  
 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] には、以下を実現する side\-by\-side ホスティングの新しい方法が用意されています。  
  
-   新しいバージョンの .NET Framework をインストールした場合に、既存のアプリケーションに影響を与えません。  
  
-   アプリケーションは、ビルドに使用されたバージョンの .NET Framework で実行されます。  新しいバージョンの .NET Framework を使用するには、そのように明示的に指示する必要があります。  ただし、新しいバージョンの .NET Framework を使用するようにアプリケーションを移行する方が簡単です。  
  
## ユーザーおよび開発者への影響  
  
-   **エンド ユーザーおよびシステム管理者**。  新しいバージョンのランタイムを個別にまたはアプリケーションと共にインストールしても、使用しているコンピューターに影響を与えないので、安心して作業できます。  既存のアプリケーションはこれまでどおり実行されます。  
  
-   **アプリケーション開発者**。  アプリケーション開発者にとって、side\-by\-side ホスティングによる影響はほとんどありません。  既定では、アプリケーションは、ビルドに使用されたバージョンの .NET Framework で常に実行されます。この点に変わりはありません。  ただし、開発者は、この動作をオーバーライドし、新しいバージョンの .NET Framework でアプリケーションを実行するように指示できます \([シナリオ 2](#scenarios) を参照してください\)。  
  
-   **ライブラリの開発者および使用者**。  side\-by\-side ホスティングでは、ライブラリ開発者が直面する互換性の問題は解決されません。  直接参照または <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> の呼び出しによってアプリケーションで直接読み込まれるライブラリでは、読み込み先の <xref:System.AppDomain> のランタイムを引き続き使用します。  サポートする必要があるすべてのバージョンの .NET Framework に対してライブラリをテストする必要があります。  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ランタイムを使用してアプリケーションをコンパイルするが、アプリケーションに以前のランタイムを使用してビルドされたライブラリが含まれている場合は、そのライブラリでも [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] ランタイムが使用されます。  ただし、以前のランタイムを使用してビルドされたアプリケーションと、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] を使用してビルドされたライブラリの場合は、強制的にアプリケーションで [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] を使用する必要があります \([シナリオ 3](#scenarios) を参照してください\)。  
  
-   **マネージ COM コンポーネントの開発者**。  これまで、マネージ COM コンポーネントは、コンピューターにインストールされている最新バージョンのランタイムを使用して自動的に実行されていました。  現在では、COM コンポーネントは、ビルドに使用されたバージョンのランタイムで実行できます。  
  
     次の表に示すように、.NET Framework Version 1.1 でビルドされたコンポーネントは、Version 4 のコンポーネントと並行して実行できますが、Version 2.0、3.0、または 3.5 では side\-by\-side ホスティングを使用できないので、これらのバージョンのコンポーネントと並行して実行することはできません。  
  
    |.NET Framework のバージョン|1.1|2.0 \- 3.5|4|  
    |---------------------------|---------|----------------|-------|  
    |1.1|該当なし|No|Yes|  
    |2.0 \- 3.5|No|該当なし|Yes|  
    |4|Yes|Yes|該当なし|  
  
> [!NOTE]
>  .NET Framework Version 3.0 および 3.5 は、Version 2.0 を基盤としてインクリメント方式で構築されており、並行して実行する必要はありません。  これらのバージョンは、本質的に同じバージョンです。  
  
<a name="scenarios"></a>   
## side\-by\-side ホスティングの一般的なシナリオ  
  
-   **シナリオ 1:** 以前のバージョンの .NET Framework でビルドされた COM コンポーネントを使用するネイティブ アプリケーション。  
  
     インストールされている .NET Framework のバージョン: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]、および COM コンポーネントで使用されるその他のすべてのバージョンの .NET Framework。  
  
     操作内容: このシナリオでは何もしません。  COM コンポーネントは、そのコンポーネントが登録されているバージョンの .NET Framework で実行されます。  
  
-   **シナリオ 2**: [!INCLUDE[net_v20SP1_short](../../../includes/net-v20sp1-short-md.md)] でビルドされたマネージ アプリケーション。[!INCLUDE[dnprdnext](../../../includes/dnprdnext-md.md)] で優先的に実行しますが、Version 2.0 がない場合は [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] で実行します。  
  
     インストールされている .NET Framework のバージョン: 以前のバージョンの .NET Framework および [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]。  
  
     操作内容: アプリケーション ディレクトリの [アプリケーション構成ファイル](../../../docs/framework/configure-apps/index.md) で、次のように設定されている [\<起動\> 要素](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md) と [\<supportedRuntime\> 要素](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md) を使用する:  
  
    ```  
    <configuration>  
      <startup >  
        <supportedRuntime version="v2.0.50727" />  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
-   **シナリオ 3:** 以前のバージョンの .NET Framework でビルドされた COM コンポーネントを使用するネイティブ アプリケーション。[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] で実行します。  
  
     インストールされている .NET Framework のバージョン: [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]。  
  
     操作内容: アプリケーション ディレクトリのアプリケーション構成ファイルで、`useLegacyV2RuntimeActivationPolicy` 属性を `true` に設定した `<startup>` 要素と次のように設定した `<supportedRuntime>` 要素を使用します。  
  
    ```  
    <configuration>  
      <startup useLegacyV2RuntimeActivationPolicy="true">  
        <supportedRuntime version="v4.0" />  
      </startup>  
    </configuration>  
    ```  
  
## 例  
 マネージ COM コンポーネントを実行するアンマネージ COM ホストの例を次に示します。マネージ COM コンポーネントの実行には、そのコンパイルで対象としたバージョンの .NET Framework を使用します。  
  
 次のコード例を実行し、次のマネージ COM コンポーネントを登録するには [!INCLUDE[net_v35_long](../../../includes/net-v35-long-md.md)]を使用してコンパイルします。  コンポーネントは、**\[プロジェクト\]** メニューに登録するには、**\[プロパティ\]** をクリックします、**\[ビルド\]** タブをクリックし、**\[COM 相互運用機能の登録\]** チェック ボックスをオンにします。  
  
```  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Runtime.InteropServices;  
  
namespace BasicComObject  
{  
    [ComVisible(true), Guid("9C99C4B5-CA54-4c58-8988-49B6811BA53B")]  
    public class MyObject : SimpleObjectModel.IPrintInfo  
    {  
        public MyObject()  
        {  
        }  
        public void PrintInfo()  
        {  
            Console.WriteLine("MyObject was activated in {0} runtime in:\n\tAppDomain {1}:{2}", System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion(), AppDomain.CurrentDomain.Id, AppDomain.CurrentDomain.FriendlyName);  
        }  
    }  
}  
```  
  
 次のアンマネージ C\+\+ アプリケーションをコンパイルします。これにより、前の例で作成される COM オブジェクトがアクティブになります。  
  
```  
#include "stdafx.h"  
#include <string>  
#include <iostream>  
#include <objbase.h>  
#include <string.h>  
#include <process.h>  
  
using namespace std;  
  
int _tmain(int argc, _TCHAR* argv[])  
{  
    char input;  
    CoInitialize(NULL) ;  
    CLSID clsid;  
    HRESULT hr;  
    HRESULT clsidhr = CLSIDFromString(L"{9C99C4B5-CA54-4c58-8988-49B6811BA53B}",&clsid);  
    hr = -1;  
    if (FAILED(clsidhr))  
    {  
        printf("Failed to construct CLSID from String\n");  
    }  
    UUID id = __uuidof(IUnknown);  
    IUnknown * pUnk = NULL;  
    hr = ::CoCreateInstance(clsid,NULL,CLSCTX_INPROC_SERVER,id,(void **) &pUnk);  
    if (FAILED(hr))  
    {  
        printf("Failed CoCreateInstance\n");  
    }else  
    {  
        pUnk->AddRef();  
        printf("Succeeded\n");  
    }  
  
    DISPID dispid;  
    IDispatch* pPrintInfo;  
    pUnk->QueryInterface(IID_IDispatch, (void**)&pPrintInfo);  
    OLECHAR FAR* szMethod[1];  
    szMethod[0]=OLESTR("PrintInfo");   
    hr = pPrintInfo->GetIDsOfNames(IID_NULL,szMethod, 1, LOCALE_SYSTEM_DEFAULT, &dispid);  
    DISPPARAMS dispparams;  
    dispparams.cNamedArgs = 0;  
    dispparams.cArgs = 0;  
    VARIANTARG* pvarg = NULL;  
    EXCEPINFO * pexcepinfo = NULL;  
    WORD wFlags = DISPATCH_METHOD ;  
;  
    LPVARIANT pvRet = NULL;  
    UINT * pnArgErr = NULL;  
    hr = pPrintInfo->Invoke(dispid,IID_NULL, LOCALE_USER_DEFAULT, wFlags,  
        &dispparams, pvRet, pexcepinfo, pnArgErr);  
    printf("Press Enter to exit");  
    scanf_s("%c",&input);  
    CoUninitialize();  
    return 0;  
}  
  
```  
  
## 参照  
 [\<startup\> 要素](../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)   
 [\<supportedRuntime\> 要素](../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)