# fast_contacts

[![fast_contacts](https://img.shields.io/pub/v/fast_contacts)](https://pub.dev/packages/fast_contacts)
[![fast_contacts](https://img.shields.io/pub/likes/fast_contacts)](https://pub.dev/packages/fast_contacts)
[![fast_contacts](https://img.shields.io/pub/points/fast_contacts)](https://pub.dev/packages/fast_contacts)
[![fast_contacts](https://img.shields.io/pub/popularity/fast_contacts)](https://pub.dev/packages/fast_contacts)

A **much** faster alternative to [contacts_service](https://pub.dev/packages/contacts_service) and [flutter_contact](https://pub.dev/packages/flutter_contact) for reading the device's contact book.

This plugin was tuned to achieve optimal performance for fetching the whole list of contacts.
Loading 1000 contacts with this plugin should take ~200ms or less depending on the device.

# Usage

To use this plugin, add `fast_contacts` as a [dependency in your `pubspec.yaml` file](https://flutter.io/platform-plugins/).

## Permissions  
### Android  
Add the following permission to your AndroidManifest.xml:  

```xml  
<uses-permission android:name="android.permission.READ_CONTACTS" />  
```

### iOS
Set the `NSContactsUsageDescription` in your `Info.plist` file  
  
```xml  
<key>NSContactsUsageDescription</key>  
<string>Description of why you need the contacts permission.</string>  
```  

**Note**
`fast_contacts` doesn't handle permissions. Use special plugins (like [permission_handler](https://pub.dartlang.org/packages/permission_handler)) to ask for the permission before accessing contacts.

## Available contact info

- ID
- Display name
- Structured name (prefix, given name, middle name, family name, suffix)
- Emails
- Phones
- Organization (company, department, job description)

## Example

```dart
// Import package  
import 'package:fast_contacts/fast_contacts.dart';  

// Get all contacts
final contacts = await FastContacts.getAllContacts();

// Get single contact by ID
final contact = await FastContacts.getContact(contactId);

// Get contact's image (thumbnail)
final thumbnail = await FastContacts.getContactImage(contact.id);

// Get contact's image (full size)
final thumbnail = await FastContacts.getContactImage(contact.id, size: ContactImageSize.fullSize);
```

For a more complete usage example, see `example` project.

## Performance

Loading 1000+ contacts (display name, structured name, phones, emails) at once takes ~200ms on both Android (Samsung Galaxy S8) and iOS (iPhone 8).

![Android: Samsung Galaxy S8](doc/images/android_screenshot.png)

![iOS: iPhone 8](doc/images/ios_screenshot.png)
