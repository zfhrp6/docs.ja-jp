---
title: セキュリティと競合状態
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfc4d9e9ba3653bd1a762767e3c39a4f62e587a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582136"
---
# <a name="security-and-race-conditions"></a>セキュリティと競合状態
問題の別の領域は、競合状態によって生じるセキュリティ ホールが発生する可能性です。 これが発生するいくつかの方法はあります。 次のサブトピックをアウトラインの主要な落とし穴を開発者が回避する必要があります。  
  
## <a name="race-conditions-in-the-dispose-method"></a>Dispose メソッドでの競合状態  
 クラスの場合**Dispose**メソッド (詳細については、次を参照してください[ガベージ コレクション](../../../docs/standard/garbage-collection/index.md)) が同期されていない可能性が内のそのクリーンアップ コード**Dispose**実行できる複数の。1 回、次の例で示すようにします。  
  
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
  
 この**Dispose**実装が同期されていない、可能性が`Cleanup`によって最初に 1 つのスレッドとし、2 番目のスレッドの前に呼び出される`_myObj`に設定されている**null**です。 動作に依存これは、セキュリティが脅かされるかどうかと、`Cleanup`コードを実行します。 非同期の主な課題**Dispose**実装は、ファイルなどのリソース ハンドルを使用します。 不適切な廃棄には、間違ったを識別するハンドルを使用する多くの場合、セキュリティの脆弱性につながる可能性があります。  
  
## <a name="race-conditions-in-constructors"></a>コンス トラクターでの競合状態  
 一部のアプリケーションでは、そのクラス コンス トラクターが完全に実行する前にクラス メンバーにアクセスするには、他のスレッドがあります。 すべてのクラス コンス トラクターがないセキュリティの問題が発生するか必要な場合は、スレッドを同期場合かどうかを確認するを参照してください。  
  
## <a name="race-conditions-with-cached-objects"></a>キャッシュされたオブジェクトの競合状態  
 セキュリティ情報をキャッシュしたり、コード アクセス セキュリティを使用するコード[Assert](../../../docs/framework/misc/using-the-assert-method.md)操作される恐れがありますも競合状態、クラスの他の部分が適切に同期していない場合、次の例に示すようにします。  
  
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
  
 その他のパスがある場合`DoOtherWork`同一のオブジェクトと別のスレッドから呼び出すことができますを過去の需要、信頼されていない呼び出し元がずれることです。  
  
 コードがセキュリティ情報をキャッシュする場合は、この脆弱性を確認することを確認します。  
  
## <a name="race-conditions-in-finalizers"></a>ファイナライザーでの競合状態  
 競合状態は、そのファイナライザーで解放し、静的またはアンマネージ リソースを参照するオブジェクトでも発生することができます。 複数のオブジェクトは、クラスのファイナライザーで操作されるリソースを共有している場合、オブジェクトは、そのリソースへのすべてのアクセスを同期する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)
