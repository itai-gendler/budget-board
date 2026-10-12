---
{
  "scope": "Web access and financial workspace handlers, retained records, monthly planning, imports, automation, provider synchronization, reporting and functional widget configuration.",
  "method": "Read-only static source, persistence, configuration and documentation inspection at source commit 816f3278c12702c2a317965724cf8346d1b11cd1.",
  "covered": [
    {
      "description": "Public access, browser session and identity management code.",
      "paths": [
        "client/src/app/Unauthorized/",
        "client/src/providers/AuthProvider/",
        "server/BudgetBoard.WebAPI/Overrides/IdentityApiEndpointRouteBuilderExtensions.cs",
        "server/BudgetBoard.WebAPI/Controllers/ApplicationUserController.cs",
        "server/BudgetBoard.WebAPI/Controllers/OidcController.cs",
        "server/BudgetBoard.WebAPI/Utils/ExternalUserProvisioningService.cs",
        "server/BudgetBoard.Service/ApplicationUserService.cs"
      ]
    },
    {
      "description": "Authenticated navigation and global synchronization/privacy controls.",
      "paths": [
        "client/src/app/Authorized/Navbar/",
        "client/src/app/Authorized/Header/",
        "client/src/app/Authorized/PageContent/PageContent.tsx"
      ]
    },
    {
      "description": "Account, Institution, dated Balance and Web recovery handlers.",
      "paths": [
        "client/src/app/Authorized/PageContent/Accounts/",
        "server/BudgetBoard.Service/AccountService.cs",
        "server/BudgetBoard.Service/InstitutionService.cs",
        "server/BudgetBoard.Service/BalanceService.cs",
        "server/BudgetBoard.WebAPI/Controllers/AccountController.cs",
        "server/BudgetBoard.WebAPI/Controllers/InstitutionController.cs"
      ]
    },
    {
      "description": "Asset, dated Value and Web recovery handlers.",
      "paths": [
        "client/src/app/Authorized/PageContent/Assets/",
        "server/BudgetBoard.Service/AssetService.cs",
        "server/BudgetBoard.Service/ValueService.cs"
      ]
    },
    {
      "description": "Custom vocabulary and built-in switch handling.",
      "paths": [
        "server/BudgetBoard.Service/AccountTypeService.cs",
        "server/BudgetBoard.Service/AssetTypeService.cs",
        "server/BudgetBoard.Service/TransactionCategoryService.cs",
        "server/BudgetBoard.Service/UserSettingsService.cs"
      ]
    },
    {
      "description": "Financial record, transfer, split, tag and shared bulk-operation code.",
      "paths": [
        "server/BudgetBoard.Service/TransactionService.cs",
        "server/BudgetBoard.Service/TagService.cs",
        "client/src/app/Authorized/PageContent/Transactions/",
        "client/src/components/BulkActionBar/",
        "client/src/helpers/transactions.ts"
      ]
    },
    {
      "description": "CSV mapping, export, queued processing, cancellation and retry code.",
      "paths": [
        "client/src/helpers/transactionImport.ts",
        "client/src/providers/TransactionImportJobProvider/",
        "server/BudgetBoard.Service/TransactionImportService.cs",
        "server/BudgetBoard.WebAPI/Jobs/TransactionImportWorker.cs"
      ]
    },
    {
      "description": "Calendar-month Budget operations, rollover and financial calculations.",
      "paths": [
        "server/BudgetBoard.Service/BudgetService.cs",
        "client/src/helpers/budgets.ts",
        "client/src/app/Authorized/PageContent/Budgets/"
      ]
    },
    {
      "description": "Account-linked Goal lifecycle and literal estimate calculations.",
      "paths": [
        "server/BudgetBoard.Service/GoalService.cs",
        "client/src/helpers/goals.ts",
        "client/src/app/Authorized/PageContent/Goals/"
      ]
    },
    {
      "description": "Saved and one-off Rule entry, operator and amount-expression handling.",
      "paths": [
        "server/BudgetBoard.Service/AutomaticRuleService.cs",
        "server/BudgetBoard.Service/Helpers/AutomaticRuleConditionHandler.cs",
        "server/BudgetBoard.Service/Helpers/AutomaticRuleActionHandler.cs",
        "server/BudgetBoard.Service/Helpers/AutomaticRuleActionValidator.cs",
        "server/BudgetBoard.Service/Helpers/AmountExpressionParser.cs"
      ]
    },
    {
      "description": "Recurring calendar, projection, amount and matching implementation.",
      "paths": [
        "server/BudgetBoard.Service/RecurringRuleService.cs",
        "server/BudgetBoard.Service/Models/RecurringCadence.cs",
        "server/BudgetBoard.Service/Helpers/RecurringRuleOccurrenceCalculator.cs"
      ]
    },
    {
      "description": "Classifier training and accepted new-record predictions.",
      "paths": [
        "server/BudgetBoard.Service/AutomaticTransactionCategorizerService.cs",
        "server/BudgetBoard.Service/Helpers/AutomaticTransactionCategorizerHelper.cs"
      ]
    },
    {
      "description": "Provider credentials, metadata, links, history, snapshots and synchronization order.",
      "paths": [
        "server/BudgetBoard.Service/SimpleFinService.cs",
        "server/BudgetBoard.Service/SimpleFinAccountService.cs",
        "server/BudgetBoard.Service/SimpleFinOrganizationService.cs",
        "server/BudgetBoard.Service/LunchFlowService.cs",
        "server/BudgetBoard.Service/LunchFlowAccountService.cs",
        "server/BudgetBoard.Service/SyncService.cs",
        "server/BudgetBoard.WebAPI/Jobs/SyncBackgroundJob.cs",
        "client/src/app/Authorized/PageContent/ExternalAccounts/"
      ]
    },
    {
      "description": "Functional widget defaults and configuration lifecycle.",
      "paths": [
        "server/BudgetBoard.Service/WidgetSettingsService.cs",
        "server/BudgetBoard.Service/Helpers/WidgetSettingsHelpers.cs",
        "client/src/app/Authorized/PageContent/Dashboard/",
        "client/src/components/ui/widgets/"
      ]
    },
    {
      "description": "Addressed net-worth configuration and recursive source calculations.",
      "paths": [
        "server/BudgetBoard.Service/NetWorthWidgetGroupService.cs",
        "server/BudgetBoard.Service/NetWorthWidgetLineService.cs",
        "server/BudgetBoard.Service/NetWorthWidgetCategoryService.cs",
        "client/src/helpers/widgets.ts"
      ]
    },
    {
      "description": "Metric expressions, source formulas and period/data requirements.",
      "paths": [
        "client/src/helpers/metricWidget.ts"
      ]
    },
    {
      "description": "Eight analysis modes, signed flow aggregation and dated snapshot charts.",
      "paths": [
        "client/src/app/Authorized/PageContent/Trends/",
        "client/src/helpers/charts.ts",
        "client/src/components/Charts/"
      ]
    },
    {
      "description": "Personal section settings, browser-local masking and shipped locales.",
      "paths": [
        "client/src/app/Authorized/PageContent/Settings/",
        "client/src/providers/PrivacyModeProvider/",
        "client/src/helpers/privacy.ts",
        "client/src/i18n/",
        "server/BudgetBoard.Service/UserSettingsService.cs"
      ]
    },
    {
      "description": "Current retained facts, ownership and deletion relationships.",
      "paths": [
        "server/BudgetBoard.Database/Models/",
        "server/BudgetBoard.Database/Data/UserDataContext.cs",
        "server/BudgetBoard.Database/Migrations/UserDataContextModelSnapshot.cs"
      ]
    },
    {
      "description": "Server deployment gates and independent browser control flags.",
      "paths": [
        "server/BudgetBoard.WebAPI/Program.cs",
        "server/BudgetBoard.WebAPI/Utils/DemoModeFilter.cs",
        "client/src/shared/projectEnvVariables.ts"
      ]
    }
  ],
  "exclusions": [
    {
      "description": "Build, deployment and CI machinery.",
      "paths": [
        ".github/",
        "client/package.json",
        "server/BudgetBoard.WebAPI/BudgetBoard.WebAPI.csproj"
      ]
    },
    {
      "description": "Historical migration execution; current relationship definitions are covered separately.",
      "paths": [
        "server/BudgetBoard.Database/Migrations/"
      ]
    },
    {
      "description": "Decorative assets and grid geometry.",
      "paths": [
        "client/src/assets/",
        "img/",
        "client/src/shared/dashboardGrid.ts"
      ]
    },
    {
      "description": "Internal synchronization locks and operational logging receipts.",
      "paths": [
        "server/BudgetBoard.Service/Helpers/NetWorthWidgetConfigurationLock.cs"
      ]
    },
    {
      "description": "Installed mapping tools and their instructions.",
      "paths": [
        ".agents/skills/"
      ]
    }
  ],
  "unmapped": [
    {
      "description": "Standalone Institution deletion contract and exhaustive direct transaction-marker branch combinations; the last-active-Account side effect is described separately.",
      "paths": [
        "server/BudgetBoard.Service/InstitutionService.cs"
      ]
    },
    {
      "description": "Permanent Asset removal outside established browser controls.",
      "paths": [
        "server/BudgetBoard.Service/AssetService.cs",
        "server/BudgetBoard.WebAPI/Controllers/AssetController.cs"
      ]
    },
    {
      "description": "Optional Account-service restore-with-transactions branch absent from the inspected Web controller.",
      "paths": [
        "server/BudgetBoard.Service/AccountService.cs"
      ]
    },
    {
      "description": "Demo data seeding and scheduled reset lifecycle.",
      "paths": [
        "server/BudgetBoard.Service/DemoSeedService.cs",
        "server/BudgetBoard.WebAPI/Jobs/DemoResetJob.cs"
      ]
    },
    {
      "description": "Application-update discovery and notification lifecycle.",
      "paths": [
        "server/BudgetBoard.WebAPI/Controllers/AppUpdateController.cs",
        "server/BudgetBoard.WebAPI/Services/AppUpdateService.cs",
        "client/src/hooks/queries/useAppUpdateQuery.ts"
      ]
    },
    {
      "description": "Identity email-change, bearer/refresh and diagnostic consumer contracts.",
      "paths": [
        "server/BudgetBoard.WebAPI/Overrides/IdentityApiEndpointRouteBuilderExtensions.cs"
      ]
    },
    {
      "description": "Complete disclosure audit across raw displays, export consumers and tooltips.",
      "paths": [
        "client/src/helpers/privacy.ts",
        "client/src/components/Charts/",
        "client/src/app/Authorized/PageContent/Transactions/"
      ]
    },
    {
      "description": "Exhaustive concurrent, stale, cyclic and arithmetic-error behavior.",
      "paths": [
        "server/BudgetBoard.Service/NetWorthWidgetCategoryService.cs",
        "client/src/helpers/widgets.ts",
        "client/src/helpers/metricWidget.ts",
        "server/BudgetBoard.Service/GoalService.cs"
      ]
    }
  ],
  "limitations": [
    {
      "description": "Goal arithmetic branches use different positive-baseline and debt predicates with incomplete arithmetic-domain guards.",
      "paths": [
        "server/BudgetBoard.Service/GoalService.cs"
      ]
    },
    {
      "description": "Financial-eligibility predicates and parent-allocation effects differ among the inspected service/helper operations.",
      "paths": [
        "server/BudgetBoard.Service/BudgetService.cs",
        "server/BudgetBoard.Service/GoalService.cs",
        "server/BudgetBoard.Service/TransactionService.cs",
        "client/src/helpers/charts.ts"
      ]
    },
    {
      "description": "Independent browser/server feature flags and validations do not establish deployment agreement.",
      "paths": [
        "server/BudgetBoard.WebAPI/Program.cs",
        "server/BudgetBoard.WebAPI/Utils/DemoModeFilter.cs",
        "client/src/shared/projectEnvVariables.ts"
      ]
    },
    {
      "description": "Name-based recursive sources and case-dependent cycle checks do not establish universally safe configurations.",
      "paths": [
        "server/BudgetBoard.Service/NetWorthWidgetCategoryService.cs",
        "client/src/helpers/widgets.ts"
      ]
    },
    {
      "description": "Metric Budget formulas and queries differ from main monthly Budget calculations.",
      "paths": [
        "client/src/helpers/metricWidget.ts",
        "client/src/helpers/budgets.ts"
      ]
    },
    {
      "description": "Outbound provider and framework-managed identity behavior exceeds repository-local evidence.",
      "paths": [
        "server/BudgetBoard.Service/SimpleFinService.cs",
        "server/BudgetBoard.Service/LunchFlowService.cs",
        "server/BudgetBoard.WebAPI/Overrides/IdentityApiEndpointRouteBuilderExtensions.cs"
      ]
    }
  ]
}
---

# Coverage
