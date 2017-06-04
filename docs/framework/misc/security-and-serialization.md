---
title: "セキュリティとシリアル化 | Microsoft Docs"
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
  - "コード セキュリティ, シリアル化"
  - "安全なコーディング, シリアル化"
  - "セキュリティ [.NET Framework], シリアル化"
  - "シリアル化, セキュリティ"
ms.assetid: b921bc94-bd3a-4c91-9ede-2c8d4f78ea9a
caps.latest.revision: 9
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 9
---
# セキュリティとシリアル化
シリアル化によって、他の方法ではアクセスできないオブジェクト インスタンス データを他のコードから参照または変更できるようになるため、シリアル化を実行するコードには、特殊なアクセス許可として、<xref:System.Security.Permissions.SecurityPermissionFlag> フラグが指定された <xref:System.Security.Permissions.SecurityPermission> が必要です。 既定のポリシーでは、インターネットからダウンロードしたコードまたはイントラネット コードにはこのアクセス許可は与えられず、ローカル コンピューター上のコードにだけ付与されます。  
  
 通常、オブジェクト インスタンスのすべてのフィールドはシリアル化されます。つまり、データは、インスタンスのシリアル化されたデータで表されます。 形式を解釈できるコードでは、メンバーのアクセシビリティとは関係なく、データ値を判断できます。 同様に、逆シリアル化でもアクセシビリティ規則に関係なく、シリアル化された表現からデータを抽出し、オブジェクトの状態を直接設定します。  
  
 機密データを含む可能性のあるオブジェクトは、可能であれば、シリアル化できないようにしてください。 そのようなオブジェクトをシリアル化しなければならない場合、機密データを保持する特定のフィールドは、シリアル化できないように維持してください。 これが不可能な場合は、このデータが、シリアル化のアクセス許可を持つあらゆるコードに公開されることに注意し、絶対に、悪質なコードがこのアクセス許可を取得できないようにしてください。  
  
 <xref:System.Runtime.Serialization.ISerializable> インターフェイスは、シリアル化インフラストラクチャでのみ使用するためのものです。 ただし、保護されていない場合、機密情報をリリースする可能性があります。**ISerializable** を実装してカスタムのシリアル化を提供する場合は、必ず次の予防措置を取ってください。  
  
-   **SerializationFormatter** アクセス許可を指定した **SecurityPermission** を要求するか、メソッドの出力で機密情報がリリースされないことを確実にして、<xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A> メソッドを明示的に保護します。 例:  
  
    ```vb  
    Public Overrides<SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)>  _ Sub GetObjectData(info As SerializationInfo, context As StreamingContext) End Sub  
  
    ```  
  
    ```csharp  
    [SecurityPermissionAttribute(SecurityAction.Demand,SerializationFormatter =true)] public override void GetObjectData(SerializationInfo info, StreamingContext context) { }  
    ```  
  
-   シリアル化に使用する特殊なコンストラクターでも徹底的な入力検証を行い、悪質なコードによる悪用を防ぐために、コンストラクターを保護するか、またはプライベートにする必要があります。 また、クラスを明示的に作成したり、ある種のファクトリで間接的に作成したりするなど、他の方法でこのようなクラスのインスタンスを取得する場合にも、同じセキュリティ チェックとアクセス許可を適用してください。  
  
## 参照  
 [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)