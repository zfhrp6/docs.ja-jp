---
title: "セキュリティと競合状態 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "コード セキュリティ, 競合状態"
  - "競合状態"
  - "安全なコーディング, 競合状態"
  - "セキュリティ [.NET Framework], 競合状態"
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# セキュリティと競合状態
競合状態によって生じるセキュリティ ホールの可能性についても考慮する必要があります。  この問題は、いくつかの状況で発生します。  開発者が注意しなければならない主な事項を、以下のサブトピックで説明します。  
  
## Dispose メソッドでの競合状態  
 クラスの **Dispose** メソッドが同期されていない場合は、**Dispose** 内のクリーンアップ コードが複数回実行されることがあります。この例を次に示します。詳細については「[Garbage Collection](../../../docs/standard/garbage-collection/index.md)」を参照してください。  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
  
```  
  
```csharp  
void Dispose()   
{  
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 この **Dispose** の実装は同期されていないため、`Cleanup` は最初のスレッドによって呼び出され、`_myObj` が **null** に設定される前に、2 番目のスレッドによって呼び出される可能性があります。  `Cleanup` コードが実行されたときに何が起こるかによって、セキュリティの問題となるかどうかが決まります。  同期されていない **Dispose** 実装で最も問題になるのが、ファイルなどのリソース ハンドルの使用についてです。  廃棄が適切でないと誤ったハンドルが使用され、これがセキュリティ脆弱性を招く可能性があります。  
  
## コンストラクターでの競合状態  
 アプリケーションによっては、クラスのコンストラクターが完全に実行される前に、他のスレッドがクラス メンバーにアクセスすることがあります。  すべてのクラスのコンストラクターを調べ、このようなことが起きてもセキュリティの問題が発生しないことを確認してください。必要であれば、スレッドを同期します。  
  
## キャッシュされたオブジェクトとの競合状態  
 セキュリティ情報をキャッシュするコード、またはコード アクセス セキュリティの [Assert](../../../docs/framework/misc/using-the-assert-method.md) 操作を使用するコードは、クラスの他の部分が適切に同期されていないと、競合状態に対する脆弱性を持ちます。この例を次に示します。  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
  
```  
  
```csharp  
void SomeSecureFunction()   
{  
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
    {  
        DoSomethingTrusted();  
    }  
    else   
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 同じオブジェクトを使用して別のスレッドから呼び出される `DoOtherWork` への別のパスがあるときは、信頼関係のない呼び出し元が要求を通してしまう可能性があります。  
  
 コードがセキュリティ情報をキャッシュする場合は、この脆弱性について確認する必要があります。  
  
## ファイナライザーでの競合状態  
 静的リソースまたはアンマネージ リソースを参照し、そのファイナライザー内で解放されるオブジェクトには、競合状態が発生する可能性があります。  クラスのファイナライザーで操作されるリソースを複数のオブジェクトで共有している場合は、オブジェクトはそのリソースへのすべてのアクセスを同期する必要があります。  
  
## 参照  
 [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)