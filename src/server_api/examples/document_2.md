---
layout: page
title: "DOCUMENT 4X-ում և 8X-ում" 
---

`UserAccounts.as` ֆայլի պարունակություն։ 4X-ում պետք է գրված լինի ANSI կոդավորմամբ։

```as4x
DOCUMENT {
  NAME = UsrAccs;
  CAPTION = "Օգտագործողի հաշիվներ";
  ECAPTION = "User's accounts";
  PROCESSINGMODE = 8; '#DocProcessingMode2

  PAGE { CAPTION = "Ընդհանուր"; ECAPTION = "General";
    REKVIZIT {NAME = USERNAME; CAPTION = "Օգտագործողի անուն"; ECAPTION="User's name";         TYPE = C(20); };
    REKVIZIT {NAME = BRANCH;   CAPTION = "Մասնաճյուղ";        ECAPTION="Registration branch"; TYPE = C(10); };

    GRID {NAME = Accounts; CAPTION = "Հաշիվներ"; ECAPTION = "Accounts"; WIDTH = 13000; HEIGHT = 3000;
      COLUMN {NAME = ACCTYPE; CAPTION = "Տիպ"; ECAPTION = "Type"; TYPE = C(10);  };
      COLUMN {NAME = CODE;    CAPTION = "Կոդ"; ECAPTION = "Code"; TYPE = NP(16); };
    };

    MEMO {NAME = COMMENT; CAPTION = "Մեկնաբանություն"; ECAPTION = "Comment"; WIDTH = 7000; HEIGHT = 2300; };
  };
};
```

`UsrAccs.CodeGen.tt` ֆայլի պարունակություն։

```tt
<#@ template debug="false" hostspecific="true" language="C#" #>
<#@ assembly name="ArmSoft.AS8X.CodeGen" #>
<#@ import namespace="ArmSoft.AS8X.CodeGen" #>
<#@ output extension=".cs" encoding="utf-8" #>
<#
	string code = DocParser.Parse(
		configFilePath: this.Host.ResolvePath(@"..\CodeGen.xml"), 
		filename: @"\Users\UserAccounts.as", 
		docType: "UsrAccs", 
		namespaceName: "Bank");
#>
<#= code #>
```

`UsrAccs.CodeGen.cs` ֆայլի պարունակություն։

```c#
// Ավտոմատ գեներացված է՝ սկիզբ
using ArmSoft.AS8X.Core;
using ArmSoft.AS8X.Core.Document;
using ArmSoft.AS8X.Common.Extensions;

namespace ArmSoft.AS8X.Bank
{
    [Document("UsrAccs")]
    public partial class UsrAccs : Document
    {
        public partial class AccountsRow : GridRow
        {
            /// <summary>
            /// Տիպ
            /// </summary>
            public string ACCTYPE
            {
                get { return (string)this[nameof(this.ACCTYPE)]; }
                set { this[nameof(this.ACCTYPE)] = value; }
            }

            /// <summary>
            /// Կոդ
            /// </summary>
            public decimal CODE
            {
                get { return (decimal)this[nameof(this.CODE)]; }
                set { this[nameof(this.CODE)] = value; }
            }

        }

        /// <summary>
        /// Հաշիվներ
        /// </summary>
        public Grid<AccountsRow> Accounts
        {
            get
            {
                return (Grid<AccountsRow>)this.Grids[nameof(this.Accounts)];
            }
        }


        // Fields
        /// <summary>
        /// Օգտագործողի անուն
        /// </summary>
        public string USERNAME
        {
            get { return (string)this[nameof(this.USERNAME)]; }
            set { this[nameof(this.USERNAME)] = value; }
        }

        /// <summary>
        /// Մասնաճյուղ
        /// </summary>
        public string BRANCH
        {
            get { return (string)this[nameof(this.BRANCH)]; }
            set { this[nameof(this.BRANCH)] = value; }
        }

        // Memos
        /// <summary>
        /// Մեկնաբանություն
        /// </summary>
        public string COMMENT
        {
            get { return GetMemo(nameof(this.COMMENT)); }
            set { SetMemo(nameof(this.COMMENT), value); }
        }
    }
}
// Ավտոմատ գեներացված է՝ վերջ
```

`UsrAccs.cs` ֆայլի պարունակություն։

```c#
using System;

namespace ArmSoft.AS8X.Bank;

public partial class UsrAccs
{
    public UsrAccs(IServiceProvider serviceProvider) : base(serviceProvider)
    {

    }
}
```
