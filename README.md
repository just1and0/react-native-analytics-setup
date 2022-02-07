# react-native-analytics-setup
a simple template for setting up Firebase Analytics in expo applications

```js
import * as Analytics from "expo-firebase-analytics";

export let Logs = {
  USER_DELETED_ACCOUNT: {
    tag: "USER_DELETED_ACCOUNT",
    label: "user deleted account",
  },
    USER_ACTIVATED_PUSH_NOTIFICATION: {
    tag: "USER_ACTIVATED_PUSH_NOTIFICATION",
    label: "user turned-on push notification",
  },
};

interface AnalyticsLogsProps {
  name: {tag:string; label:string};
  userId: string;
  screen?: string;
}

type name =
  | "USER_DELETED_ACCOUNT"
  | "USER_ACTIVATED_PUSH_NOTIFICATION ;

const AnalyticsLogs = (props: AnalyticsLogsProps) => {
  let { tag, label } = props.name;
  if (props.name) {
    Analytics.logEvent(tag, {
      user: props.userId,
      screen: props?.screen || "EVENT_LOG_TRACK",
      purpose: label,
    });
  } else {
    console.log("ops something went wrong logging this event.");
  }
};
export default AnalyticsLogs;

```


# usage 

```js
import AnalyticsLogs, { Logs } from "./utils/analytics";

AnalyticsLogs({name:Logs.USER_ACTIVATED_PUSH_NOTIFICATION, userId:'123'})
```
