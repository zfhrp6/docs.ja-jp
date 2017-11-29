---
title: "方法 : 信頼できるセッション内でメッセージをセキュリティで保護する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 3f27b1a4de2019660e0facb081300a79eae65b99
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>方法 : 信頼できるセッション内でメッセージをセキュリティで保護する

ここでは、信頼できるセッション内で交換されるメッセージに対して、メッセージ レベルのセキュリティを有効にするために必要な手順について説明します。このとき、信頼できるセッションがオプションでサポートされているシステム指定のバインディングを使用します。 コードを使用して強制的に行うか、宣言、構成ファイルでは、セキュリティで保護された信頼できるセッションを有効にします。 この手順では、クライアントとサービスの構成ファイルを使用して、セキュリティで保護された信頼できるセッションを有効にします。

この手順の主な部分は、次の 3 つの作業で構成されます。

1. クライアントとサービスのメッセージ交換は信頼できるセッション内で行うことを指定します。

1. 信頼できるセッション内でメッセージ レベルのセキュリティを要求します。

1. サービスに対する認証時にクライアントが使用する必要があるクライアント資格情報を指定します。

エンドポイント構成要素を含む最初のタスクで重要な`bindingConfiguration`に (この例の) という名前のバインディング構成を参照する属性を`MessageSecurity`です。 [ **\<バインディング >** ](../../../../docs/framework/misc/binding.md)構成要素を設定して、信頼できるセッションを有効にするには、この名前を参照し、`enabled`の属性、 [  **\<reliableSession >** ](http://msdn.microsoft.com/en-us/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)要素を`true`です。 信頼できるセッション内で使用できる順序付き配信の保証は、`ordered` 属性を `true` に設定することによって要求できます。

この構成手順を基になる例の元のコピーを次を参照してください。、 [WS 信頼できるセッション](../../../../docs/framework/wcf/samples/ws-reliable-session.md)です。

設定して行われます 2 番目のタスクの重要な項目、`mode`の属性、 **\<セキュリティ >**要素に含まれている、 **\<バインディング >** 。要素のクライアントとサービスを`Message`です。

設定して行われます 3 番目のタスクの重要な項目、`clientCredentialType`の属性、 **\<メッセージ >**要素に含まれている、 **\<セキュリティ >** 。要素のクライアントとサービスを`Certificate`です。

> [!NOTE]
> メッセージ セキュリティを使用して、信頼できるセッションで、最初のエラー発生時に例外をスローする代わりに、タイムアウトが発生するまでは、認証されていないクライアントを認証すると信頼性の高いメッセージングされます。

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>信頼できるセッションを使用する WSHttpBinding でサービスを構成します。

この手順で説明されて[する方法: Exchange メッセージ内で、信頼できるセッション](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)です。

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>信頼できるセッションを使用する WSHttpBinding でクライアントを構成します。

この手順で説明されて[する方法: Exchange メッセージ内で、信頼できるセッション](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md)です。

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>構成でモードと ClientCredentialType を設定します。

1. 適切なバインド要素を追加、 [ **\<バインド >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)構成ファイルの要素。 次の例では追加、 [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)要素。

1. 追加、 **\<バインディング >**要素とその`name`属性を適切な値にします。 例では、名前を使用して`MessageSecurity`です。

1. 追加、 **\<セキュリティ >**要素、`mode`属性を`Message`です。

1. 内で、 **\<セキュリティ >**要素を追加、 **\<メッセージ >**要素、`clientCredentialType`属性を`Certificate`です。

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
