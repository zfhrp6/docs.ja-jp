---
title: "セキュリティの基本概念 | Microsoft Docs"
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
  - "アクセス許可 [.NET Framework]"
  - "セキュリティ [.NET Framework], セキュリティの概要"
  - "不正侵入"
ms.assetid: 3cfced4f-ea02-4e66-ae98-d69286363e98
caps.latest.revision: 22
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 20
---
# セキュリティの基本概念
Microsoft .NET Framework では、セキュリティ透過、コード アクセス セキュリティ、およびロールベース セキュリティを使用できます。これらのセキュリティ機構は、モバイル コードに関するセキュリティ上の処理に役立ち、各ユーザーにどのような権限を与えるかをコンポーネントで決定できるようにします。  これらのセキュリティ機構は単純で一貫性のあるモデルを使用するため、コード アクセス セキュリティの知識がある開発者は、ロール ベース セキュリティを簡単に使用できます。また、ロール ベース セキュリティの知識がある開発者も、コード アクセス セキュリティを簡単に使用できます。  コード アクセス セキュリティとロール ベース セキュリティのいずれも、共通言語ランタイムによって提供される共通のインフラストラクチャを使用して実装されます。  
  
> [!NOTE]
>  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、セキュリティ透過が既定の適用機構になっています。  セキュリティ透過によって、アプリケーションの一部として実行されるコードがインフラストラクチャの一部として実行されるコードから分離されます。  詳しくは、「[透過的セキュリティ コード](../../../docs/framework/misc/security-transparent-code.md)」をご覧ください。  
  
 コード アクセス セキュリティとロール ベース セキュリティは、同じモデルとインフラストラクチャを使用するため、基になる概念のいくつかが共通します。ここでは、これらの概念について説明します。  .NET Framework のコード アクセス セキュリティとロール ベース セキュリティの説明を読む前に、これらの共通概念について理解しておいてください。  
  
## セキュリティ アクセス許可  
 共通言語ランタイムを使用すると、コードが実行できる操作を、実行するためのアクセス許可をそのコードが持つ操作だけに限定できます。  ランタイムはアクセス許可と呼ばれるオブジェクトを使用して、マネージ コードに制限を課します。  ランタイムは、いくつかの名前空間の中に組み込みアクセス許可クラスを備えているほか、カスタムのアクセス許可クラスのデザインおよび実装をサポートします。  
  
 アクセス許可には次の 2 種類があり、それぞれ固有の目的があります。  
  
-   コード アクセス許可は、保護されているリソースに対するアクセス権や、保護されている操作を実行する権限を表します。  
  
-   ロール ベースのセキュリティ権限により、ユーザー \(またはユーザーのために行動するエージェント\) が特定の ID を持っているかどうか、または特定のロールに所属しているかどうかを検出するメカニズムが実現されます。  <xref:System.Security.Permissions.PrincipalPermission> が、唯一のロール ベース セキュリティ アクセス許可です。  
  
 セキュリティ アクセス許可は、アクセス許可クラス \(強制セキュリティ\) の形式か、アクセス許可クラスを表す属性 \(宣言セキュリティ\) の形式にできます。  セキュリティ アクセス許可の基本クラスは <xref:System.Security.CodeAccessPermission?displayProperty=fullName> で、セキュリティ アクセス許可属性の基本クラスは <xref:System.Security.Permissions.CodeAccessSecurityAttribute?displayProperty=fullName> です。  
  
 アセンブリの形式のアプリケーションには、アプリケーション ドメインに読み込まれるときに一連のアクセス許可が付与されます。  この付与は、通常、<xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=fullName> メソッドによって決定される定義済みのアクセス許可セットを使用して行われます。  許可セットにより、コードが利用できるアクセス許可が決まります。  ランタイムは、コードの生成場所 \(ローカル コンピューター、ローカル イントラネット、インターネットなど\) に基づいてアクセス許可を与えます。  コードがサンドボックスに読み込まれる場合は、コードに特別なアクセス許可を付与することもできます。  サンドボックスにおけるコードの実行について詳しくは、「[方法 : サンドボックスで部分信頼コードを実行する](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)」をご覧ください。  
  
 アクセス許可の主な用途は次のとおりです。  
  
-   ライブラリ コードは、呼び出し元が特定のアクセス許可を持つことを確認要求できます。  コードにアクセス許可に対する <xref:System.Security.CodeAccessPermission.Demand%2A> を配置すると、そのコードを使用するすべてのコードは、実行するときにそのアクセス許可が必要になります。  確認要求は、呼び出し元が特定のリソースへのアクセス権を有するかどうかを判断したり、呼び出し元の身元を調査したりするために使用できます。  
  
-   コードでは、アクセス許可を使用して、保護するリソースへのアクセスを拒否できます。  <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> を使用すると、制限されたアクセス許可セットを指定して、他のすべてのアクセス許可を暗黙的に拒否できます。  ただし、意図的な悪用を防ぐ目的で <xref:System.Security.Permissions.SecurityAction> を使用してアクセスを禁止することはお勧めしません。  暗黙的に拒否されたアクセス許可を許可セット内に有する呼び出されたアセンブリは、使用するアクセス許可に対して <xref:System.Security.Permissions.SecurityAction?displayProperty=fullName> を実行することにより、拒否されたアクセス許可をオーバーライドできます。  たとえば、<xref:System.Security.Permissions.UIPermission> のみを許可し、本来 <xref:System.Security.Permissions.FileIOPermission> を持つアセンブリを呼び出した場合、アセンブリは <xref:System.Security.Permissions.FileIOPermission> に対して <xref:System.Security.Permissions.SecurityAction> を実行するだけで、ファイル操作を実行できるようになります。  参照されたアセンブリ内の信頼できないコードからリソースを安全に保護する唯一の方法は、そのコードを、それらのアクセス許可を含まない許可セットにより実行することです。  
  
### コード アクセス許可  
 コード アクセス許可は、リソースと操作が権限なしに使用されないように保護するアクセス許可オブジェクトです。  コード アクセス許可は、マネージ コードにセキュリティ制限を適用するための共通言語ランタイムの機構の基本的な部分です。  
  
 各コード アクセス許可は、次の権限のいずれかを表します。  
  
-   ファイルや環境変数など、保護されたリソースにアクセスする権限。  
  
-   アンマネージ コードへのアクセスなど、保護された操作を実行するための権限。  
  
 すべてのコード アクセス許可は、コードで要求または確認要求できます。コードに与えられる許可の種類は、ランタイムが決定します。  
  
 各コード アクセス許可は、<xref:System.Security.CodeAccessPermission> クラスから派生します。つまり、すべてのコード アクセス許可には、**Demand**、**Assert**、**Deny**、**PermitOnly**、**IsSubsetOf**、**Intersect**、および **Union** などの共通のメソッドがあります。  
  
> [!IMPORTANT]
>  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] では、<xref:System.Security.Permissions.SecurityAction>、<xref:System.Security.Permissions.SecurityAction>、<xref:System.Security.Permissions.SecurityAction>、<xref:System.Security.Permissions.SecurityAction> の各アクセス許可要求を適用するためのランタイム サポートは削除されています。  これらの要求は、[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降に基づくコードで使用しないでください。  この点と他の変更内容について詳しくは、「[セキュリティの変更点](../../../docs/framework/security/security-changes.md)」をご覧ください。  
  
### ロール ベース セキュリティ アクセス許可  
 <xref:System.Security.Permissions.PrincipalPermission> はロール ベース セキュリティ アクセス許可で、ユーザーが指定の ID を持っているかどうか、特定のロールのメンバーかどうかを判別するのに使用できます。  **PrincipalPermission** は、.NET Framework クラス ライブラリに用意されている唯一のロール ベース セキュリティ アクセス許可です。  
  
## タイプ セーフとセキュリティ  
 タイプ セーフなコードは、アクセス権限を与えられているメモリ位置にだけアクセスします。  この場合のタイプ セーフとは、メモリのタイプ セーフの意味です。広い意味でのタイプ セーフと混同しないでください。 たとえば、タイプ セーフなコードは、他のオブジェクトのプライベート フィールドから値を読み取ることができません。  適切に定義された許容される方法でだけ、タイプにアクセスします。  
  
 ジャスト イン タイム \(JIT: Just\-In\-Time\) コンパイル時に、オプションの検査プロセスは、ネイティブなマシン コードに JIT コンパイルされるメソッドのメタデータと Microsoft Intermediate Language \(MSIL\) を調べて、タイプ セーフかどうかを確認します。  コードに検査を省略するためのアクセス許可がある場合、このプロセスは省略されます。  検査の詳細については、「[マネージ実行プロセス](../../../docs/standard/managed-execution-process.md)」を参照してください。  
  
 タイプ セーフの検査はマネージ コードの実行に必須ではありませんが、アセンブリの分離とセキュリティの適用において、タイプ セーフであることが重要な意味を持ちます。  コードがタイプ セーフであると、共通言語ランタイムはアセンブリを互いに完全に分離できます。  アセンブリが互いに分離していると、アセンブリどうしが悪い影響を及ぼしあうことがなく、アプリケーションの信頼性が向上します。  タイプ セーフなコンポーネントは、信頼されるレベルが異なっていても、同じプロセスで安全に実行できます。  コードがタイプ セーフでないと、望ましくない副作用が生じることがあります。  たとえば、ランタイムは、マネージ コードがネイティブ \(アンマネージ\) コードにアクセスしたり、不正な操作を実行することを防止できません。  コードがタイプ セーフであると、ランタイムのセキュリティ適用機構によって、必要なアクセス許可を持たないコードがネイティブ コードにアクセスすることはできません。  タイプ セーフでないすべてのコードは、列挙子メンバー <xref:System.Security.Permissions.SecurityPermission> が渡された <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A> を与えられていないと実行できません。  
  
 詳細については、「[NIB: Writing Verifiably Type\-Safe Code](http://msdn.microsoft.com/ja-jp/d18f10ef-3b48-4f47-8726-96714021547b)」をご覧ください。  
  
## プリンシパル  
 プリンシパルは、ユーザーの ID とロールを表し、ユーザーの代わりを務めます。  .NET Framework のロール ベース セキュリティでは、次の 3 種類のプリンシパルがサポートされています。  
  
-   汎用プリンシパルは、Windows のユーザーとロールとは無関係に存在するユーザーとロールを表します。  
  
-   Windows プリンシパルは、Windows のユーザーとそのロール \(または Windows グループ\) を表します。  Windows プリンシパルは、他のユーザーを偽装できます。つまり、Windows プリンシパルは、あるユーザーに属する ID を提示し、そのユーザーの代わりにリソースにアクセスできます。  
  
-   カスタム プリンシパルは、アプリケーションが必要に応じて自由に定義できます。  カスタム プリンシパルによって、プリンシパルの ID とロールの基本概念を拡張できます。  
  
 詳しくは、「[プリンシパル オブジェクトと ID オブジェクト](../../../docs/standard/security/principal-and-identity-objects.md)」をご覧ください。  
  
## 認証  
 認証とは、ユーザーの資格情報を調べ、資格情報をなんらかの権限に対して検証することによって、プリンシパルの身元 を発見および確認するプロセスです。  認証時に得られる情報は、コードで直接使用できます。  また、.NET Framework のロール ベース セキュリティを使用して、現在のユーザーを認証したり、そのプリンシパルにコードへのアクセスを許可するかどうかを判断したりできます。  特定のロールに関してプリンシパルを認証する方法の例については、<xref:System.Security.Principal.WindowsPrincipal.IsInRole%2A?displayProperty=fullName> メソッドのオーバーロードを参照してください。  たとえば、<xref:System.Security.Principal.WindowsPrincipal.IsInRole%28System.String%29?displayProperty=fullName> オーバーロードを使用すると、現在のユーザーが Administrators グループのメンバーであるかどうかを判断できます。  
  
 さまざまな認証メカニズムが現在使用されていて、その多くを .NET Framework のロール ベース セキュリティと一緒に使用できます。  最も一般に使用されている認証機構としては、基本認証、ダイジェスト認証、パスポート認証、オペレーティング システム認証 \(NTLM 認証や Kerberos 認証など\)、およびアプリケーション定義の認証機構などがあります。  
  
### 例  
 以下の例では、アクティブ プリンシパルが管理者である必要があります。  `name` パラメーターは `null` で、これにより、管理者ユーザーがこの確認要求を渡すことを許可されます。  
  
> [!NOTE]
>  Windows Vista では、ユーザー アカウント制御 \(UAC: User Account Control\) でユーザーの権限が決定されます。  ユーザーが組み込みの Administrators グループのメンバーである場合、そのユーザーには標準ユーザー アクセス トークンおよび管理者アクセス トークンの 2 つのランタイム アクセス トークンが割り当てられています。  既定では、ユーザーは標準ユーザー ロールに所属します。  管理者であることを要求するコードを実行するには、最初に、ユーザーの権限を標準ユーザーから管理者に昇格させる必要があります。  この操作は、アプリケーションの起動時にアプリケーション アイコンを右クリックし、管理者として実行することを指定して行うことができます。  
  
 [!code-cpp[Classic PrincipalPermission Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CPP/source.cpp#1)]
 [!code-csharp[Classic PrincipalPermission Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/CS/source.cs#1)]
 [!code-vb[Classic PrincipalPermission Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_Classic/classic PrincipalPermission Example/VB/source.vb#1)]  
  
 次の例は、プリンシパルの ID と、プリンシパルで使用できるロールを判別する方法を示しています。  この例のアプリケーションは、現在のユーザーがアプリケーションの使用を許可するロールに含まれていることを確認できます。  
  
 [!code-cpp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CPP/source.cpp#1)]
 [!code-csharp[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/CS/source.cs#1)]
 [!code-vb[System.Security.Principal.WindowsBuiltInRole Example#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Security.Principal.WindowsBuiltInRole Example/VB/source.vb#1)]  
  
## 承認  
 承認とは、要求されたアクションの実行をプリンシパルに許可するかどうかを判断するプロセスです。  承認は認証の後に行われ、プリンシパルの ID とロールについての情報を使用して、そのプリンシパルがアクセスできるリソースを判断します。  承認は、.NET Framework のロール ベース セキュリティを使用して実装できます。  
  
## Internal Virtual キーワードのセキュリティ関連事項  
 アプリケーションのセキュリティは、C\# の [internal](../Topic/internal%20\(C%23%20Reference\).md) [virtual](../Topic/virtual%20\(C%23%20Reference\).md) 修飾子 \(Visual Basic の [Overloads](../Topic/Overloads%20\(Visual%20Basic\).md) [Overridable](../Topic/Overridable%20\(Visual%20Basic\).md) [Friend](../Topic/Friend%20\(Visual%20Basic\).md) 修飾子\) でマークされているメンバーに基づいて構築しないでください。  これらの修飾子でマークされたメンバーは、現在のアセンブリ内の他のメンバーによってのみオーバーライドされますが、この規則は C\# 言語と Visual Basic 言語だけによって強制されています。  ランタイムはこの規則を強制しません。  このため、Microsoft Intermediate Language \(MSIL\) やこの規則を強制しない言語を使用すると、C\# で **internal virtual** としてマークされたメンバーおよび Visual Basic で **Overloads Overridable Friend** としてマークされたメンバーがオーバーライドされる可能性があります。  
  
## 参照  
 [セキュリティの基本概念](../../../docs/standard/security/key-security-concepts.md)