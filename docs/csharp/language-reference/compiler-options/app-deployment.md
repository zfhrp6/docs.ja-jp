---
title: "Deployment of C# Applications | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
  - "CSharp"
helpviewer_keywords: 
  - "deploying applications [C#]"
  - "Visual C#, deployment"
  - "C# language, deployment"
  - "application deployment [C#]"
ms.assetid: 5c561a21-cc5b-4180-8042-391062af0015
caps.latest.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 9
---
# Deployment of C# Applications
C\# アプリケーションをビルドしたら、いよいよ、アプリケーションを配布することになります。  C\# は .NET 言語であるため、C\# の実行可能ファイルを他のコンピューターに配布するには、配布先の各コンピューターに .NET Framework が \(場合によっては、アプリケーションに固有の依存ファイルも\) インストールされている必要があります。  .NET Framework の配布方法としては、さまざまな選択肢が用意されています。  概要については、「[配置ガイド \(開発者向け\)](../Topic/.NET%20Framework%20Deployment%20Guide%20for%20Developers.md)」を参照してください。  
  
 一般に、完成したアプリケーションを他のコンピューターに移動することを、"配置" と呼びます。  Microsoft の開発環境では、配置に必要なしくみが用意されています。詳細については、「[アプリケーションとコンポーネントの配置](/visual-studio/deployment/deploying-applications-services-and-components)」を参照してください。  
  
 ビルドおよび配布作業をコマンド ラインから行う機会が多い場合、アプリケーションの配置と、依存関係を持つファイルの再配布には、これ以外の方法を検討する必要があります。  
  
## 参照  
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)