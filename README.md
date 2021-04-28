# Eatvo

## Can Be Better

* There is no **filename standard** in this app. There are **three** different filename types.
  * FileName.dart
  * file_name.dart
  * fileName.dart

* There is no **foldername standard** in this app. There are **three** different foldername types.
  * folderName.dart
  * folder-name.dart
  * folderName-other.dart

* **Localization** folder <ins>should not</ins> be under the lib folder.

* There are too many **unnecessary new files** in the project. *Some widgets should be private instead of public.*

* There is no **analysis tool** in this project. **Dart-Linter** tools *(like [flutrlint](https://pub.dev/packages/flutrlint))* can help to make this project cleaner and better. It also helps to create a standard for the project.

* There are two different **State Management** method.
  * Provider
  * GetX

## Wrong Usage

* ### The member '**notifyListeners**' can only be used within 'package:flutter/src/foundation/change_notifier.dart' or a test. [invalid_use_of_visible_for_testing_member]
  * lib/src/controllers/**cart_controller.dart**
      * 73
          ```dart
              cart.notifyListeners();
          ```
      * 83
          ```dart
              cart.notifyListeners();
          ```
      * 140
          ```dart
              cart.notifyListeners();
          ```
      * 361
          ```dart
              cart.notifyListeners();
          ```
      * 394
          ```dart
              cart.notifyListeners();
          ```
      * 433
          ```dart
              cart.notifyListeners();
          ```
      * 446
          ```dart
              cart.notifyListeners();
          ```
      * 461
          ```dart
              cart.notifyListeners();
          ```
  * lib/src/controllers/**category_controller.dart**
      * 360
          ```dart
              globalController.cart.notifyListeners();
          ```
  * lib/src/controllers/**checkout_controller.dart**
      * 155
          ```dart
              globalController.cart.notifyListeners();
          ```
  * lib/src/controllers/**favorite_controller.dart**
      * 122
          ```dart
              globalController.cart.notifyListeners();
          ```
  * lib/src/controllers/**notification_controller.dart**
      * 38
          ```dart
              notifications.notifyListeners();
          ```
      * 65
          ```dart
              notifications.notifyListeners();
          ```
  * lib/src/controllers/**product_controller.dart**
      * 247
          ```dart
              globalController.cart.notifyListeners();
          ```
  * lib/src/elements/**LanguageItemWidget.dart**
      * 79
          ```dart
              globalController.setting.notifyListeners();
          ```
  * lib/src/repository/**settings_repository.dart**
      * 76
          ```dart
              globalController.setting.notifyListeners();
          ```
  * lib/src/repository/**user_repository.dart**
      * 338
          ```dart
              globalController.currentUser.notifyListeners();
          ```

* ### The member '**notifyListeners**' can only be used within instance members of subclasses of 'package:flutter/src/foundation/change_notifier.dart'. [invalid_use_of_protected_member]
  * lib/src/controllers/**cart_controller.dart**
      * 73
          ```dart
              cart.notifyListeners();
          ```
      * 83
          ```dart
              cart.notifyListeners();
          ```
      * 140
          ```dart
              cart.notifyListeners();
          ```
      * 361
          ```dart
              cart.notifyListeners();
          ```
      * 394
          ```dart
              cart.notifyListeners();
          ```
      * 433
          ```dart
              cart.notifyListeners();
          ```
      * 446
          ```dart
              cart.notifyListeners();
          ```
      * 461
          ```dart
              cart.notifyListeners();
          ```
  * lib/src/controllers/**category_controller.dart**
      * 360
          ```dart
              globalController.cart.notifyListeners();
          ```
  * lib/src/controllers/**checkout_controller.dart**
      * 155
          ```dart
              globalController.cart.notifyListeners();
          ```
  * lib/src/controllers/**favorite_controller.dart**
      * 122
          ```dart
              globalController.cart.notifyListeners();
          ```
  * lib/src/controllers/**notification_controller.dart**
      * 38
          ```dart
              notifications.notifyListeners();
          ```
      * 65
          ```dart
              notifications.notifyListeners();
          ```
  * lib/src/controllers/**product_controller.dart**
      * 247
          ```dart
              globalController.cart.notifyListeners();
          ```
  * lib/src/elements/**LanguageItemWidget.dart**
      * 79
          ```dart
              globalController.setting.notifyListeners();
          ``` 
  * lib/src/repository/**settings_repository.dart**
        * 76
            ```dart
                globalController.setting.notifyListeners();
            ```
  * lib/src/repository/**user_repository.dart**
      * 338
          ```dart
              globalController.currentUser.notifyListeners();
          ```

* ### Cancel instances of **`dart.async.StreamSubscription`**. => [cancel_subscriptions](https://dart-lang.github.io/linter/lints/cancel_subscriptions.html)
  * lib/src/controllers/**tracking_controller.dart**
      * 30
          ```dart
          /// Cancelling instances of StreamSubscription prevents memory leaks and unexpected behavior.
          StreamSubscription orderStream;
          ```
  * lib/src/pages/**location_tracker.dart**
      * 30
          ```dart
          /// Cancelling instances of StreamSubscription prevents memory leaks and unexpected behavior.
          StreamSubscription subscription;
          ```

* ### Close instances of **`dart.core.Sink`**. => [close_sinks](https://dart-lang.github.io/linter/lints/close_sinks.html)
  * lib/src/pages/**location_tracker.dart**
      * 30
          ```dart
          /// Closing instances of Sink prevents memory leaks and unexpected behavior.
          BehaviorSubject<double> radius = BehaviorSubject();
          ```

* ### Avoid using **unnecessary statements**. => [unnecessary_statements](https://dart-lang.github.io/linter/lints/unnecessary_statements.html)
  * lib/src/elements/GalleryCarouselWidget.dart
    * 42
      ```dart
      /// Statements which have no clear effect are usually unnecessary, or should be broken up.
      widget.images != null
              ? CachedNetworkImage(
                  fit: BoxFit.fill,
                  imageUrl: widget.images.elementAt(0),
                  placeholder: (context, url) => Image.asset(
                      'assets/img/loading.gif',
                      fit: BoxFit.cover,
                  ),
                  errorWidget: (context, url, error) => Icon(Icons.error),
                )
              : null;
  * lib/src/elements/GalleryCarouselWidget.dart
    * 42
        ```dart
        /// Statements which have no clear effect are usually unnecessary, or should be broken up.
        onTap: () {
            speech.isListening ? null : startListening();
        },
        ```

* ### This class (or a class that this class inherits from) is marked as '**@immutable**', but one or more of its instance fields aren't final: => [must_be_immutable]
  * lib/src/elements/**NotificationItemWidget.dart**
      * 6
          ```dart
          class NotificationItemWidget extends StatelessWidget {
              model.Notification notification; // It should be final

              NotificationItemWidget({Key key, this.notification}) : super(key: key);
          ```
  * lib/src/elements/**NotifyUnavailableProductDialog.dart**
      * 10
          ```dart
          class NotifyProductDialog extends StatefulWidget {
              BuildContext context;
              RouteArgument routeArgument;
              Product product;
              final GlobalKey<ScaffoldState> scaffoldstate = new GlobalKey<ScaffoldState>();
          ```
  * lib/src/elements/**PaymentSettingsDialog.dart**
      * 6
          ```dart
          class PaymentSettingsDialog extends StatefulWidget {
            CreditCard creditCard;
            VoidCallback onChanged;
          ```
  * lib/src/elements/**ProductsCarouselItemWidget.dart**
      * 7
          ```dart
          class ProductsCarouselItemWidget extends StatelessWidget {
            double marginLeft;
            Product product;
            String heroTag;
          ```
  * lib/src/elements/**ProductsCarouselWidget.dart**
      * 6
          ```dart
          class FoodsCarouselWidget extends StatelessWidget {
            List<Product> foodsList;
            String heroTag;
          ```
        The name of the file is `ProductsCarouselWidget` but the name of the class is `FoodsCarouselWidget`.
  * lib/src/elements/**ProfileSettingsDialog.dart**
      * 9
        ```dart
        class ProfileSettingsDialog extends StatefulWidget {
            UserModel user;
            VoidCallback onChanged;
        ```
  * lib/src/elements/**SearchResultsCardWidget.dart**
      * 7
        ```dart
        class SearchResultsCardWidget extends StatelessWidget {
            Product product;
            String heroTag;
        ```
  * lib/src/elements/**SearchResultsWidget.dart**
      * 18
        ```dart
        class SearchResultWidget extends StatefulWidget {
            String heroTag;
        ```
  * lib/src/elements/**SimilarProductCarouselItemWidget.dart**
      * 11
        ```dart
        class SimilarProductCarouselItemWidget extends StatelessWidget {
            double marginLeft;
            Product product;
            String heroTag;
        ```
  * lib/src/elements/**SimilarProductCarouselWidget.dart**
      * 8
        ```dart
        class SimilarProductCarouselWidget extends StatelessWidget {
            List<Product> similarProductsList;
            String heroTag;
        ```
  * lib/src/helpers/maps/**AddressCardWidget.dart**
      * 6
        ```dart
        class AddressCardWidget extends StatefulWidget {
            String heroTag;
        ```
  * lib/src/pages/**kuponautomata.dart**
      * 18
        ```dart
        class KuponAutomata extends StatefulWidget {
            UserModel user = new UserModel();
            VoidCallback onChanged;
            final couponTerms = GlobalConfiguration().getValue('mobile_base_url') +
                "coupon/terms?lang=${globalController.setting.value.mobileLanguage.value.languageCode}";
            GlobalKey<ScaffoldState> scaffoldKey;
        ```

* ### This function has a return type of '*Widget | String* ', but doesn't end with a return statement. [missing_return]
  * lib/**route_generator.dart**
    * 55
      ```dart
      class RouteGenerator {
        static Route<dynamic> generateRoute(RouteSettings settings) {
      ```
  * lib/src/elements/**NotifyUnavailableProductDialog.dart**
    * 39
      ```dart
      @override
      Widget build(BuildContext context) {
          AwesomeDialog(
          context: context,
          dialogType: DialogType.INFO,
          animType: AnimType.RIGHSLIDE,
          title: S.of(context).do_you_want_us_to_notify_when_it_is_in_stock_again,
          desc: "",
          btnOkOnPress: () {
              _con.notifyAboutProduct(widget.product);
              Navigator.pop(context);
          },
          btnCancelOnPress: () {
              Navigator.pop(context);
          },
          btnCancelText: S.current.cancel,
          btnOkColor: Theme.of(context).accentColor,
          btnCancelColor: Color(0xFF084457).withOpacity(0.9),
          )..show();
      }
      ```
  * lib/src/elements/**ProfileSettingsDialog.dart**
    * 73
        ```dart
        validator: (value) {
            if (value.isEmpty)
                return S.of(context).should_not_be_empty;
            if (value.length < 5)
                return S.of(context).min_length_should_be("5");
            if (!Helper.emailValidator(value))
                return S.of(context).should_be_a_valid_email;
        },
        ```

* ### The declaration isn't referenced. [unused_element]
  * lib/src/elements/**OrderReviewDialog.dart**
    * 155
      ```dart
      double _rating;
      ```

* ### The value of the field isn't used. [unused_field]
  * lib/src/elements/**SpinningWheelWidget.dart**
    * 134
      ```dart
      RenderBox _renderBox;
      ```
  * lib/src/helpers/maps/**map.dart**
    * 77
      ```dart
      String _addressId = "";
      ```

* ### The value of the local variable '_marginLeft' isn't used. [unused_local_variable]
  * lib/src/pages/**search.dart**
    * 194
      ```dart
      itemBuilder: (context, index) {
        double _marginLeft = 0;
        (index == 0)
            ? _marginLeft = 20
            : _marginLeft = 0;
      ```

* ### Deprecated Member Usage [deprecated_member_usage]
  * lib/src/elements/**PaymentSettingsDialog.dart**
    * 186
    ```dart
    /// 'hasFloatingPlaceholder' is deprecated and shouldn't be used. Use floatingLabelBehavior instead. This feature was deprecated after v1.13.2..
    ///
    /// Try replacing the use of the deprecated member with the replacement.
    hasFloatingPlaceholder: true,
    ```
  * lib/src/elements/**ProfileAvatarWidget.dart**
    * 75
    ```dart
    /// 'headline' is deprecated and shouldn't be used. This is the term used in the 2014 version of material design. 
    ///
    /// The modern term is headline5. This feature was deprecated after v1.13.8..
    Text(
        user.name,
        style: Theme.of(context)
            .textTheme
            .headline
            .merge(TextStyle(color: Theme.of(context).primaryColor)),
    ),
    ```
  * lib/src/elements/**ProfileSettingsDialog.dart**
    * 142
    ```dart
    /// 'hasFloatingPlaceholder' is deprecated and shouldn't be used. Use floatingLabelBehavior instead. This feature was deprecated after v1.13.2..
    ///
    /// Try replacing the use of the deprecated member with the replacement.
    hasFloatingPlaceholder: true,
    ```
  * lib/src/helpers/**checkbox_form_field.dart**
    * 15
    ```dart
    CheckboxFormField(
      {Widget title,
      @required BuildContext context,
      FormFieldSetter<bool> onSaved,
      FormFieldValidator<bool> validator,
      bool initialValue = false,
      bool autovalidate = false})
      : super(
            onSaved: onSaved,
            validator: validator,
            initialValue: initialValue,
            /// 'autovalidate' is deprecated and shouldn't be used. Use autoValidateMode parameter which provides more specific behavior related to auto validation. This feature was deprecated after v1.19.0..
            /// Try replacing the use of the deprecated member with the replacement.
            autovalidate: autovalidate,
            builder: (FormFieldState<bool> state) {
              return CheckboxListTile(
                dense: state.hasError,
                title: title,
                value: state.value,
                onChanged: state.didChange,
                subtitle: state.hasError
                    ? Text(
                        state.errorText,
                        style: TextStyle(color: Theme.of(context).errorColor),
                      )
                    : null,
                controlAffinity: ListTileControlAffinity.leading,
              );
            });
    ```
  * lib/src/elements/**cart_invoice_address.dart**
      * 236
      ```dart
      /// ''autovalidate' is deprecated and shouldn't be used. Use autoValidateMode parameter which provide more specific behaviour related to auto validation. This feature was deprecated after v1.19.0..
      ///
      /// Try replacing the use of the deprecated member with the replacement.
      TextFormField(
        controller: _phoneController,
        // initialValue: phone,
        validator: (input) => input.length < 7
            ? S
                .of(context)
                .message_phone_number_length
            : null,
        onSaved: (input) => globalController
            .cart
            .value
            .invoiceAddress
            .phoneNo = input,
        inputFormatters: [
            ModifiedLengthLimitingTextInputFormatter(
                64),
        ],
        autovalidate: false,
        autocorrect: false,
        maxLengthEnforced: true,
        keyboardType: TextInputType.phone,
        decoration: InputDecoration(
            labelStyle: TextStyle(
                color: Theme.of(context)
                    .accentColor),
            contentPadding: EdgeInsets.all(12),
            hintStyle: TextStyle(
                color: Theme.of(context)
                    .focusColor
                    .withOpacity(0.7)),
            prefixIcon: Icon(Icons.phone,
                size: 30,
                color: Theme.of(context)
                    .accentColor),
            border: OutlineInputBorder(
                borderSide: BorderSide(
                    color: Theme.of(context)
                        .focusColor
                        .withOpacity(0.2))),
            focusedBorder: OutlineInputBorder(
                borderSide: BorderSide(
                    color: Theme.of(context)
                        .focusColor
                        .withOpacity(0.5))),
            enabledBorder: OutlineInputBorder(
                borderSide: BorderSide(
                    color: Theme.of(context)
                        .accentColor
                        .withOpacity(0.2))),
            hintText: S.of(context).phone,
            ),
        ),
      ```
  * lib/src/pages/**order_report.dart**
      * 52
      ```dart
      /// 'pickImage' is deprecated and shouldn't be used. Use imagePicker.getImage() method instead..
      ///
      /// Try replacing the use of the deprecated member with the replacement.
      void _selectNewImage(int index) async {
        var image = await ImagePicker.pickImage(source: ImageSource.gallery, imageQuality: 85);
      ```
  * lib/src/pages/phone-auth/**otp_input.dart**
      * 1014
      ```dart
        /// 'autovalidate' is deprecated and shouldn't be used. Use autoValidateMode parameter which provides more specific behavior related to auto validation. This feature was deprecated after v1.19.0..
        ///
        /// Try replacing the use of the deprecated member with the replacement.
        PinInputTextFormField({
            Key key,
            this.controller,
            String initialValue,
            this.pinLength = 6,
            ValueChanged<String> onSubmit,
            PinDecoration decoration = const BoxLooseDecoration(),
            List<TextInputFormatter> inputFormatter,
            TextInputType keyboardType = TextInputType.phone,
            FocusNode focusNode,
            bool autoFocus = false,
            TextInputAction textInputAction = TextInputAction.done,
            bool enabled = true,
            FormFieldSetter<String> onSaved,
            FormFieldValidator<String> validator,
            bool autovalidate = false,
            ValueChanged<String> onChanged,
        })  : assert(initialValue == null || controller == null),
                assert(autovalidate != null),
                assert(pinLength != null && pinLength > 0),
                super(
                    key: key,
                    initialValue:
                        controller != null ? controller.text : (initialValue ?? ''),
                    onSaved: onSaved,
                    validator: (value) {
                    var result = validator(value);
                    if (result == null) {
                        if (value.isEmpty) {
                        return 'Input field is empty.';
                        }
                        if (value.length < pinLength) {
                        if (pinLength - value.length > 1) {
                            return 'Missing ${pinLength - value.length} digits of input.';
                        } else {
                            return 'Missing last digit of input.';
                        }
                        }
                    }
                    return result;
                    },
                    autovalidate: autovalidate,
                    enabled: enabled,
                    builder: (FormFieldState<String> field) {
                    final _PinInputTextFormFieldState state = field;
                    return PinInputTextField(
                        pinLength: pinLength,
                        onSubmit: onSubmit,
                        decoration: decoration.copyWith(errorText: field.errorText),
                        inputFormatter: inputFormatter,
                        keyboardType: keyboardType,
                        controller: state._effectiveController,
                        focusNode: focusNode,
                        autoFocus: autoFocus,
                        textInputAction: textInputAction,
                        enabled: enabled,
                        onChanged: onChanged,
                    );
                    });
      ```
  * lib/src/pages/phoneVerification-auth/**VerificationOtp_input.dart**
      * 1014
        ```dart
        /// 'autovalidate' is deprecated and shouldn't be used. Use autoValidateMode parameter which provides more specific behavior related to auto validation. This feature was deprecated after v1.19.0..
        ///
        /// Try replacing the use of the deprecated member with the replacement.
        PinInputTextFormField({
            Key key,
            this.controller,
            String initialValue,
            this.pinLength = 6,
            ValueChanged<String> onSubmit,
            PinDecoration decoration = const BoxLooseDecoration(),
            List<TextInputFormatter> inputFormatter,
            TextInputType keyboardType = TextInputType.phone,
            FocusNode focusNode,
            bool autoFocus = false,
            TextInputAction textInputAction = TextInputAction.done,
            bool enabled = true,
            FormFieldSetter<String> onSaved,
            FormFieldValidator<String> validator,
            bool autovalidate = false,
            ValueChanged<String> onChanged,
        }) : assert(initialValue == null || controller == null),
                assert(autovalidate != null),
                assert(pinLength != null && pinLength > 0),
                super(
                    key: key,
                    initialValue:
                        controller != null ? controller.text : (initialValue ?? ''),
                    onSaved: onSaved,
                    validator: (value) {
                    var result = validator(value);
                    if (result == null) {
                        if (value.isEmpty) {
                        return 'Input field is empty.';
                        }
                        if (value.length < pinLength) {
                        if (pinLength - value.length > 1) {
                            return 'Missing ${pinLength - value.length} digits of input.';
                        } else {
                            return 'Missing last digit of input.';
                        }
                        }
                    }
                    return result;
                    },
                    autovalidate: autovalidate,
                    enabled: enabled,
                    builder: (FormFieldState<String> field) {
                    final _PinInputTextFormFieldState state = field;
                    return PinInputTextField(
                        pinLength: pinLength,
                        onSubmit: onSubmit,
                        decoration: decoration.copyWith(errorText: field.errorText),
                        inputFormatter: inputFormatter,
                        keyboardType: keyboardType,
                        controller: state._effectiveController,
                        focusNode: focusNode,
                        autoFocus: autoFocus,
                        textInputAction: textInputAction,
                        enabled: enabled,
                        onChanged: onChanged,
                    );
                    });
        ```
  * lib/src/pages/phoneVerificationCar/**CartVerificationOtp_input.dart**
      * 1014
      ```dart
        /// 'autovalidate' is deprecated and shouldn't be used. Use autoValidateMode parameter which provides more specific behavior related to auto validation. This feature was deprecated after v1.19.0..
        ///
        /// Try replacing the use of the deprecated member with the replacement.
        PinInputTextFormField({
            Key key,
            this.controller,
            String initialValue,
            this.pinLength = 6,
            ValueChanged<String> onSubmit,
            PinDecoration decoration = const BoxLooseDecoration(),
            List<TextInputFormatter> inputFormatter,
            TextInputType keyboardType = TextInputType.phone,
            FocusNode focusNode,
            bool autoFocus = false,
            TextInputAction textInputAction = TextInputAction.done,
            bool enabled = true,
            FormFieldSetter<String> onSaved,
            FormFieldValidator<String> validator,
            bool autovalidate = false,
            ValueChanged<String> onChanged,
        })  : assert(initialValue == null || controller == null),
                assert(autovalidate != null),
                assert(pinLength != null && pinLength > 0),
                super(
                    key: key,
                    initialValue:
                        controller != null ? controller.text : (initialValue ?? ''),
                    onSaved: onSaved,
                    validator: (value) {
                    var result = validator(value);
                    if (result == null) {
                        if (value.isEmpty) {
                        return 'Input field is empty.';
                        }
                        if (value.length < pinLength) {
                        if (pinLength - value.length > 1) {
                            return 'Missing ${pinLength - value.length} digits of input.';
                        } else {
                            return 'Missing last digit of input.';
                        }
                        }
                    }
                    return result;
                    },
                    autovalidate: autovalidate,
                    enabled: enabled,
                    builder: (FormFieldState<String> field) {
                    final _PinInputTextFormFieldState state = field;
                    return PinInputTextField(
                        pinLength: pinLength,
                        onSubmit: onSubmit,
                        decoration: decoration.copyWith(errorText: field.errorText),
                        inputFormatter: inputFormatter,
                        keyboardType: keyboardType,
                        controller: state._effectiveController,
                        focusNode: focusNode,
                        autoFocus: autoFocus,
                        textInputAction: textInputAction,
                        enabled: enabled,
                        onChanged: onChanged,
                    );
                    });
        ```
  * lib/src/pages/**product_review.dart**
      * 37
      ```dart
      /// 'pickImage' is deprecated and shouldn't be used. Use imagePicker.getImage() method instead..
      ///
      /// Try replacing the use of the deprecated member with the replacement.
      void _selectNewImage(int index) async {
        var image = await ImagePicker.pickImage(source: ImageSource.gallery, imageQuality: 85);
      ```
  * lib/src/pages/**profile.dart**
      * 535
      ```dart
      /// 'pickImage' is deprecated and shouldn't be used. Use imagePicker.getImage() method instead..
      ///
      /// Try replacing the use of the deprecated member with the replacement.
        if (imageSource != null) {
            final file = await ImagePicker.pickImage(source: imageSource);
            if (file != null) {
                setState(() => _pickedImage = file);
            // setState(() => _pickedImageFile = file.);
                _upload();
            }
        }
      ```
     * 585
      ```dart
        /// 'pickImage' is deprecated and shouldn't be used. Use imagePicker.getImage() method instead..
        ///
        /// Try replacing the use of the deprecated member with the replacement.
        _loadPicker(ImageSource source) async {
            File picked = await ImagePicker.pickImage(source: source);
            if (picked != null) {
            _cropImage(picked);
            }
            Navigator.pop(context);
        }
      ```

* ### Avoid using braces in interpolation when not needed. [unnecessary_brace_in_string_interps](https://dart-lang.github.io/linter/lints/unnecessary_brace_in_string_interps.html)
  * lib/src/elements/**ShareWidget.dart**
    * 31
    ```dart
    /// If you're just interpolating a simple identifier, and it's not immediately followed by more alphanumeric text, the {} can and should be omitted.
    final String text = "${product.name} - ${eatvoUrl}";
    ```

* ### Name non-constant identifiers using lowerCamelCase. [non_constant_identifier_names](https://dart-lang.github.io/linter/lints/non_constant_identifier_names.html)
  * lib/src/helpers/**map_util.dart**
    * 8
    ```dart
    /// Class members, top-level definitions, variables, parameters, named parameters and named constructors should capitalize the first letter of each word except the first word, and use no separators.
    static final BASE_URL = "https://maps.googleapis.com/maps/api/directions/json?";
    ```

* ### The parameter is required [missing_required_param]
  * lib/**route_generator.dart**
    * 134
    ```dart
    /// The parameter 'mobileNumberReg' is required.
    case '/SignUp':
        return MaterialPageRoute(builder: (_) => SignUpWidget());
        break;
    ```
  * lib/src/pages/phone-auth/**otp_screen.dart**
    * 365
    ```dart
    /// The parameter 'mobileNumberReg' is required.
    MaterialPageRoute(
        builder: (context) => SignUpWidget(
            user: value.user,
        ),
    ),
    ```

## Pubspec Issues

  * ### Incorrect type. Expected "dependencies". [yaml-schema: Pubspec]
    ```yaml
    dependencies:
        flutter:
            sdk: flutter
        flutter_localizations:
            sdk: flutter

        # The following adds the Cupertino Icons font to your application.
        # Use with the CupertinoIcons class for iOS style icons.
        cupertino_icons: ^0.1.2
        flutter_swiper: ^1.1.6
        google_maps_flutter: ^0.5.26+4
        mvc_pattern: ^3.4.1
        global_configuration: ^1.3.0
        http: ^0.12.0+2
        intl: ^0.16.0
        html: ^0.14.0+2
        shared_preferences: ^0.5.6
        flutter_html: ^0.10.4
        flutter_svg: ^0.18.0
        location: ^2.3.5
        dynamic_theme: ^1.0.0
        url_launcher: ^5.4.1
        cached_network_image: 2.0.0-rc
        font_awesome_flutter: ^8.8.1

        # FireBase packages
        firebase_dynamic_links: any
        firebase_messaging: ^7.0.3
        firebase_analytics: ^5.0.9
        firebase_auth: ^0.18.4+1
        cloud_firestore: ^0.14.0+2
        firebase_core: ^0.5.3
        firebase_crashlytics: any
        awesome_dialog:
            git:
            url: https://github.com/panaszok/awesomeDialogs.git
        curved_navigation_bar: ^0.3.2
        provider: ^4.3.1
        flutter_inner_drawer: ^0.5.5
        carousel_pro: ^1.0.0
        flutter_login_facebook: ^0.4.0+1 # For Android
        flutter_launcher_icons: ^0.7.4
        carousel_slider: ^2.1.0
        package_info: ^0.4.0+16
        android_intent: ^0.3.6+1
        geolocator: ^6.2.0
        google_sign_in: ^4.4.1
        indexed_list_view: ^1.0.8
        share: ^0.6.3+6
        flutter_widgets: ^0.1.12
        giffy_dialog: ^1.7.0
        flutter_open_whatsapp: ^0.1.2
        flutter_rating_bar: ^3.2.0+1
        image_cropper: ^1.3.0
        image_picker: ^0.6.3+1
        apple_sign_in: ^0.1.0
        device_info: ^1.0.0
        file_picker: ^1.9.0+1
        flutter_polyline_points: ^0.2.4
        flutter_web_browser: ^0.11.0
        flutter_slidable: ^0.5.4
        badges: ^1.1.1
        barcode_scan: ^1.0.0
        form_field_validator: ^1.0.1
        international_phone_input: ^1.0.4
        intl_phone_number_input: ^0.5.2+2
        permission_handler: ^4.2.0
        lazy_load_scrollview: ^1.1.0
        flutter_inappwebview: ^4.0.0+4
        flare_flutter: ^2.0.5
        smart_flare: any
        marquee: ^1.5.2
        instabug_flutter:
        flutter_blurhash: ^0.5.0
        connectivity: ^0.4.9+2
        facebook_app_events: ^0.8.1
        data_connection_checker: ^0.3.4
        progress_dialog: ^1.2.4
        flushbar: ^1.10.4
        speech_to_text: ^2.7.0
        animations: ^1.1.2
        flutter_staggered_animations: ^0.1.2
        avatar_glow: ^1.2.0
        flutter_sliding_up_panel: ^1.1.0+1
        get: ^3.24.0
        deep_link_navigation: ^1.3.1
        custom_sheet: ^0.1.1+4
        chips_choice: ^2.0.1
        flutter_launcher_name: ^0.0.1
        flutter_spinkit: ^4.1.2
        location_permissions: ^3.0.0+1
        #quick_actions: ^0.4.0+10

        dev_dependencies:
    ```
    dev_dependies should not be empty! Some of the packages used should be under the `dev_dependencies` like:
      * [```flutter_launcher_name: ^0.0.1```](https://pub.dev/packages/flutter_launcher_name)
      * [```flutter_launcher_icons: ^0.7.4```](https://pub.dev/packages/flutter_launcher_icons)
  
  * ### Unnecessary or Unsupported Packages
    * Because of some unsupported old packages, the version of the project **cannot/will not** be updated and it is not possible to migrate the project to the **Null Safety**. Some of these packages:
      * [```flutter_launcher_name: ^0.0.1```](https://pub.dev/packages/flutter_launcher_name) Last Update: Sep 20, 2019
      * [```flutter_open_whatsapp: ^0.1.2```](https://pub.dev/packages/flutter_open_whatsapp) Last Update: Jul 3, 2019
      * [```deep_link_navigation: ^1.3.1```](https://pub.dev/packages/deep_link_navigation) Last Update: Dec 30, 2019
    
    * Some of the packages are unnecessary. It is pretty easy to do it manually.
      * ```flutter_open_whatsapp```
      * ```flutter_launcher_name```

    * [**Awesome Dialog**](https://pub.dev/packages/awesome_dialog) package is used from [github](https://pub.dev/packages/awesome_dialog). *Probably the packages is changed from a developer. Why?*
