# MUI-tabs
Integrating route configuration with material ui tabs

Material UI Tabs with route configured.

    import React from 'react';
    import {Tabs, Tab} from 'material-ui/Tabs';
    import {Link,hashHistory} from 'react-router';

    import ComponentOne from '../path/to/componentOne'
    import ComponentTwo from '../path/to/componentTwo'
    import ComponentThree from '../path/to/componentThree'
    import ComponentFour from '../path/to/componentFour'

    export default class MaterialUiTab extends React.Component {
      
      // Create JSX component and add onChange() as well as value attribute. 
      // _routeConfig() will push hashHistory & _getCurrentTab will fetch current tab index.
      
      render(){
        return (
          <div>
            <Tabs onChange = {this._routeConfig.bind(this)} value={this._getCurrentTab()}>
              <Tab label="Sub Route4" value = {0}>
                <ComponentOne />
              </Tab>
              <Tab label="Sub Route1" value = {1}>
                <ComponentTwo />
              </Tab>
              <Tab label="Sub Route2" value = {2}>
                <ComponentThree />
              </Tab>
              <Tab label="Sub Route3" value = {3}>
                <ComponentFour />
              </Tab>
            </Tabs>
          </div>
        );
      }
    
    // This method will help in routing tabs to subsequent hashHistory
      _routeConfig(selectedIndex){
        switch (selectedIndex) {
          case 0:
            hashHistory.push('/route/subRoute1');
            break;
          case 1:
            hashHistory.push('/route/subRoute2');
            break;
          case 2:
            hashHistory.push('/route/subRoute3');
            break;
          case 3:
            hashHistory.push('/route/subRoute4');
            break;
          default:
            hashHistory.push('/route/');
        }
      }

    // This method will match the subRoute and return the respective tab's index.
    
      _getCurrentTab(){
        var route = this.props.params.subRoute;
        switch (route) {
          case 'subRoute1':
            return 0;
            break;
          case 'subRoute2':
            return 1;
            break;
          case 'subRoute3':
            return 2;
            break;
          case 'subRoute4':
            return 3;
            break;
          default:
            return 0;
        }
      }
    }

