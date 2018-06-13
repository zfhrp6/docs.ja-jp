---
title: リンク確認要求
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], demands
- demanded permissions
- permissions [.NET Framework], demands
- granting permissions, demands
- code access security, demands
- user demands for permission
- caller security checks
- link demands
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 29a3254bb5ccfe422a1c2d7d156975c0887d9273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390664"
---
# <a name="link-demands"></a>リンク確認要求
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 リンク確認要求では、Just-In-Time コンパイル時にセキュリティ チェックが実行され、コードの直前の呼び出し元アセンブリだけがチェックされます。 リンクは、コードを関数ポインターの参照やメソッドの呼び出しなどの型の参照にバインドするときに発生します。 呼び出し元のアセンブリが、コードにリンクするための十分な権限を持たない場合は、リンクは許可されず、コードが読み込まれて実行されると、ランタイム例外がスローされます。 リンク確認要求は、コードから継承するクラスでオーバーライドできます。  
  
 この種類の要求では、完全なスタック ウォークが実行されないことと、コードがおびき寄せによる攻撃を受ける可能性があることに注意してください。 たとえば、アセンブリ A 内のメソッドがリンク確認要求によって保護されている場合、直接の呼び出し元アセンブリ B はに基づいて評価されますアセンブリ B のアクセス許可 ただし、リンク確認要求には、評価が行われませんアセンブリ C のメソッドを間接的に呼び出すメソッド、メソッドを使用して、アセンブリ B. でアセンブリの場合リンク確認要求では、即時呼び出し元のアセンブリでは、呼び出し元コードにリンクを直接のアクセス許可のみを指定します。 すべての呼び出し元がコードを実行するために必要なアクセス許可は指定しません。  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>、<xref:System.Security.CodeAccessPermission.Deny%2A>、および <xref:System.Security.CodeAccessPermission.PermitOnly%2A> の各スタック ウォーク修飾子は、リンク確認要求の評価に影響を与えません。  リンク確認要求は、スタック ウォークを実行しないため、スタック ウォーク修飾子はリンク確認要求に影響を与えません。  
  
 リンク確認要求によって保護されたメソッドへのアクセスがを通じて[リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)、リンク確認要求は、リフレクションを使用してアクセスされたコードの直前の呼び出し元をチェックします。 これは、メソッドの探索と、リフレクションを使用して行うメソッド呼び出しの両方に該当します。 たとえば、コードでは、リフレクションを使用して、返します、<xref:System.Reflection.MethodInfo>オブジェクトのメソッドを表すリンク確認要求によって保護されていることを渡します**MethodInfo**するその他のコードを元のメソッドを呼び出すオブジェクトを使用するオブジェクト。 ここではリンク確認要求のチェックは 2 回に発生します。 を返すコードに対して 1 回、 **MethodInfo**オブジェクトとを呼び出すコードに 1 回です。  
  
> [!NOTE]
>  静的クラスのコンストラクターで実行されるリンク確認要求では、静的コンストラクターは保護されません。これは、静的コンストラクターがアプリケーションのコードの実行パスの外側で、システムによって呼び出されるためです。 その結果、リンク確認要求がクラス全体に適用される場合、静的コンストラクターへのアクセスは保護できませんが、クラスの残りの部分は保護されます。  
  
 次のコード フラグメントでは、`ReadData` メソッドにリンクするコードはすべて `CustomPermission` のアクセス許可を持つ必要があることを宣言によって指定しています。 このアクセス許可は架空のカスタム許可であり、.NET Framework には実在しません。 渡すことによって、確認要求が行われた、 **SecurityAction.LinkDemand**フラグを`CustomPermissionAttribute`です。  
  
```vb  
<CustomPermissionAttribute(SecurityAction.LinkDemand)> _  
Public Shared Function ReadData() As String  
    ' Access a custom resource.  
End Function    
```  
  
```csharp  
[CustomPermissionAttribute(SecurityAction.LinkDemand)]  
public static string ReadData()  
{  
    // Access a custom resource.  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [属性](../../../docs/standard/attributes/index.md)  
 [コード アクセス セキュリティ](../../../docs/framework/misc/code-access-security.md)
