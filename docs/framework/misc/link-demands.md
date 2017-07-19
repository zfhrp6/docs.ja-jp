---
title: "リンク確認要求 | Microsoft Docs"
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
  - "呼び出し元のセキュリティ チェック"
  - "コード アクセス セキュリティ, 要求"
  - "要求されるアクセス許可"
  - "付与 (アクセス許可の), 要求"
  - "リンク確認要求"
  - "アクセス許可 [.NET Framework], 要求"
  - "セキュリティ [.NET Framework], 要求"
  - "ユーザー要求 (アクセス許可に対する)"
ms.assetid: a33fd5f9-2de9-4653-a4f0-d9df25082c4d
caps.latest.revision: 18
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# リンク確認要求
リンク確認要求では、Just\-In\-Time コンパイル時にセキュリティ チェックが実行され、コードの直前の呼び出し元アセンブリだけがチェックされます。  リンクは、コードを関数ポインターの参照やメソッドの呼び出しなどの型の参照にバインドするときに発生します。  呼び出し元のアセンブリが、コードにリンクするための十分な権限を持たない場合は、リンクは許可されず、コードが読み込まれて実行されると、ランタイム例外がスローされます。  リンク確認要求は、コードから継承するクラスでオーバーライドできます。  
  
 この種類の要求では、完全なスタック ウォークが実行されないことと、コードがおびき寄せによる攻撃を受ける可能性があることに注意してください。  たとえば、アセンブリ A 内のメソッドがリンク確認要求によって保護されている場合は、アセンブリ B の直接の呼び出し元が、アセンブリ B のアクセス許可に基づいて評価されます。  ただし、リンク確認要求は、アセンブリ C がアセンブリ B のメソッドを使用してアセンブリ A のメソッドを間接的に呼び出す場合は、アセンブリ C のメソッドを評価しません。  リンク確認要求は、直前の呼び出し元アセンブリにある直接の呼び出し元がコードにリンクするために必要なアクセス許可のみを指定します。  すべての呼び出し元がコードを実行するために必要なアクセス許可は指定しません。  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A>、<xref:System.Security.CodeAccessPermission.Deny%2A>、および <xref:System.Security.CodeAccessPermission.PermitOnly%2A> の各スタック ウォーク修飾子は、リンク確認要求の評価に影響を与えません。  リンク確認要求は、スタック ウォークを実行しないため、スタック ウォーク修飾子はリンク確認要求に影響を与えません。  
  
 リンク確認要求で保護されているメソッドが[リフレクション](../../../docs/framework/reflection-and-codedom/reflection.md)経由でアクセスする場合、リンク確認要求ではリフレクションによってアクセスされたコードの直前の呼び出し元を確認します。  これは、メソッドの探索と、リフレクションを使用して行うメソッド呼び出しの両方に該当します。  たとえば、コードがリフレクションを使用して、リンク確認要求で保護されたメソッドを表す <xref:System.Reflection.MethodInfo> オブジェクトを返してから、その **MethodInfo** オブジェクトを元のメソッドを呼び出すオブジェクトを使用する別のコードに渡すと仮定してください。  この場合、リンク確認要求のチェックは 2 回発生します。1 回は **MethodInfo** オブジェクトを返すコードに対して、もう 1 回はこのオブジェクトを呼び出すコードに対してです。  
  
> [!NOTE]
>  静的クラスのコンストラクターで実行されるリンク確認要求では、静的コンストラクターは保護されません。これは、静的コンストラクターがアプリケーションのコードの実行パスの外側で、システムによって呼び出されるためです。  その結果、リンク確認要求がクラス全体に適用される場合、静的コンストラクターへのアクセスは保護できませんが、クラスの残りの部分は保護されます。  
  
 次のコード フラグメントでは、`ReadData` メソッドにリンクするコードはすべて `CustomPermission` のアクセス許可を持つ必要があることを宣言によって指定しています。  このアクセス許可は架空のカスタム許可であり、.NET Framework には実在しません。  リンク確認要求は、**SecurityAction.LinkDemand** フラグを `CustomPermissionAttribute` に渡して実行します。  
  
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
  
## 参照  
 [属性](../../../docs/standard/attributes/index.md)   
 [コード アクセス セキュリティ](../../../docs/framework/misc/code-access-security.md)