# Preparation
Before using the APP Framework to manage application resource permissions, the application developer needs to make corresponding configuration to the application. The preparation work includes defining application permissions, installing EnOS Web SDK to configure permissions, and deploying the application online.

## Defining application permissions
EnOS system defines application resources as application access controls, which are also called application permissions. Each application permission is granted an ID, which is also defined as "Element ID" in the APP Framework. Therefore, resources can be assigned to different users through application authorization. Application developers can plan and define application permissions according to the business requirements and user roles of the application. With the defined application permissions, the system administrator or organization administrator can configure applications in the APP Framework.

The following table shows how to define application permissions:

| Permission name           | Permission ID (Element ID) | Permission type |
| ------------------------- | -------------------------- | --------------- |
| Monitor menu              | menu.monitor               | Menu            |
| Report menu               | menu.report                | Menu            |
| Monitor #1 view           | monitor.1                  | UI View         |
| Monitor #2 view           | monitor.2                  | UI View         |
| Monitor #3 view           | monitor.3                  | UI View         |
| Diagnostic Report button  | button.dis_report          | UI View         |
| Generation field          | report.generation          | Data            |
| Severity field            | report.severity            | Data            |
| Boiler Efficiency section | view.boiler                | Data            |
| HP Heater Input Ratio     | view.hp_heater             | Data            |
| Condenser Undercooling    | view.condenser             | Data            |

## Configuring application permissions
After defining application permissions, install and use EnOS Web SDK to configure the application.

### Installing EnOS Web SDK

URL for downloading the EnOS Web SDK on npm: [http://npm.envisioncn.com/package/@enos/portalsdk](http://npm.envisioncn.com/package/@enos/portalsdk)

Use the following command to install EnOS Web SDK:

```
npm install @enos/portalsdk --save
```

### API

The APP Framework provides APIs for application management. Applications can retrieve user information and control page operations through the EnOS Web SDK.

Calling the APIs requires importing the portalSdk module.

```
import portalSdk from '@enos/portalsdk';
```

For the complete list of APIs and API function details, see [SDK Readme](http://npm.envisioncn.com/package/@enos/portalsdk).

### Defining menu permissions

Add permissions with the type `Menu` in the App management module and assign corresponding application permissions to specific users. After logging in the system, users can get all the assigned permissions through the `getPermissions` API, including the configured `Menu` permission.

EnOS Web SDK provides the React `Menu` component, which supports unified display of menus with input of menu data and current user permissions. Application developers can use either the `Menu` component or customize menus with permission definition.

##### Parameters of the `Menu` component

| Property     | Description                     | Type     |
| ------------ | ------------------------------- | -------- |
| menus        | Collection of menu data         | array    |
| permissions  | Permissions of the current user | array    |
| onSelectMenu | Callback for selected menu      | function |
| theme        | Key of the current theme        | string   |

##### Sample code for the `Menu` component

```
import portalSdk from '@enos/portalsdk';
import Menu from '@enos/portalsdk/lib/Menu';

class Demo extends React.Component {
    render() {
        return (
          <Menu
              menus={customMenu}
              permissions={portalSdk.getPermissions()}
              onSelectMenu={this.onSelectMenu}
              theme={portalSdk.getTheme()} />   );
  }
}

ReactDOM.render(<Demo />, mountNode);
```

##### Menu data type of the `Menu` component

```
[
  {
    id: 'category_admin',
    title: 'Admin',
    children: [
      {
        id: 'app_user_admin_menu_company',
        title: 'Company Mgmt',
        link: '/admin/company.html'
      },
      {
        id: 'app_user_admin_menu_ouadmin',
        title: 'OU Administrator',
        link: '/admin/ouadminlist.html'
      },
      {
        id: 'app_user_admin_menu_sysapp',
        title: 'Sys App Mgmt',
        link: '/admin/sysapp.html'
      }
    ]
  }
]
```

### Defining UI view permissions

Add the `meta-enos-view-id` attribute for elements that need `View` access control and set the permission ID as the value of the attribute.

Add permissions with the type `View` in the App management module and assign corresponding application permissions to specific users.

If users do not have the `View` permission, the `UI View` will not be visible to the users. To reserve page render place for this kind of `UI View`, add the `meta-enos-view-reserve=‘true’` attribute for the element. 

##### Configuration sample for elements

```
 <!-- Do not display at all -->
 <div meta-enos-view-id='qwerty'>I am control point</div>
 <!-- Reserve placeholder -->
 <div meta-enos-view-id='qwerty' meta-enos-view-reserve='true'>I am reserved control point</div>
```

### Defining data permissions

Get the list of data permissions.

```
portalSdk.getDataPermissions();
```

##### Response sample

```
[
  {
    "permissionId": 0,
    "elementId": "model.name",
    "permissionName": "model_name",
    "permissionType": 2,
    ...
  },
  {
    "permissionId": 1,
    "elementId": "model.phone",
    "permissionName": "model_phone",
    "permissionType": 2,
    ...
  }
]
```

## Deploying application

Deploy the application online when application permissions are configured. The application URL is required when system administrator or organization administrator registers the application on the APP Framework. 